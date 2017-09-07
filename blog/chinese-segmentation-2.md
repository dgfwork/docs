title: 中文分词（二）
date: 2013-12-27 09:30:34
categories: 机器学习
tags:
---
* [《中文分词（一）》](http://zipperary.com/2013/12/25/chinese-segmentation/)
* [《中文分词（二）》](http://zipperary.com/2013/12/27/chinese-segmentation-2/)
* [《中文分词（三）》](http://zipperary.com/2013/12/27/chinese-segmentation-3/)



接上文[《中文分词（一）》](http://zipperary.com/2013/12/25/chinese-segmentation/)继续介绍中文分词。

###Dict to Trie

**结巴分词源码中附带了一个 dict.txt 文件，是分词的基础：**

* 2万多条词。
* 根据北大语料、人民日报1998 语料、小说（用张华平老师的ICTCLAS进行分词）得到。
* 可加入用户自定义词典。
* 无dict亦可，用HMM也可实现分词。

dict.txt 的内容如图：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1eby0f7c9a4j20v50h5ta6.jpg)

其中第一列是 word，第二列是词频，第三列是词性（pos）。


**什么是 Trie?**

Trie 又称前缀树或字典树，是一种数据结构，可以大大提高词典的查询速度。下图是一个简单的 Trie：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1eby0iikaeuj208a083jrk.jpg)

可以看到，不同的词汇中相通前缀共享同一个节点，如「阿根廷」和「阿胶」共享「阿」。这种结构可以缩短树的深度，因而检索可以非常快。

<!--more-->

怎样用 Python 表示这种数据结构呢？我们用嵌套的 dict 类型：

下面是`foobar foobah fooxar foozap fooza`完全插入后的效果：

```
{'f' => {
           'o' => {
                    'o' => {
                             'b' => {
                                      'a' => {
                                               'h' => {
                                                        '' => 1
                                                      },
                                               'r' => {
                                                        '' => 1
                                                      }
                                             }
                                    },
                             'x' => {
                                      'a' => {
                                               'r' => {
                                                        '' => 1
                                                      }
                                             }
                                    },
                             'z' => {
                                      'a' => {
                                               '' => 1,
                                               'p' => {
                                                        '' => 1
                                                      }
                                             }
                                    }
                           }
                  }
         }
}

```

我们这一个步骤的目的就是将 dict.txt 转换为一个 trie 结构的对象，方面之后的查询。在 Python 中，用这个函数：

```python
def gen_trie(f_name):
    return trie, lfreq,ltotal
```

输入参数是 dict.txt 文件，输出一个 trie 对象，一个 lfreq记录每个词的词频，一个 ltotal 记录总共的词数。我们还要将 lfreq 转为 FREQ：

```python
FREQ = dict([(k,log(float(v)/total)) for k,v in FREQ.iteritems()]) #normalize
```
有两个好处：

1. 方便之后计算TF-IDF，以实现关键词提取的功能。
2. P(x)P(y) => logP(x) + logP(y)  #避免浮点下溢

###文本预处理

就是用正则表达式，将输入的 text，根据标点符号等，切分为由中文、英文、数字和几个特殊符号组成的短语：

```python
re_han = re.compile(ur"([\u4E00-\u9FA5a-zA-Z0-9+#&\._]+)", re.U)
```

例如 `“这是一个伸手不见五指的黑夜。我叫孙悟空，我爱北京，我爱Python和C++。”`经过这个步骤就切分为：`这是一个伸手不见五指的黑夜/我叫孙悟空/我爱北京/我爱Python和C++/`。

###短语的词图扫描

对于短语`我们都是中国人`，先从0依次编号为0-6.从左到右，依次查 trie，如「我」在 trie 中，则标记一下，「我们」也在 trie 中，再标记，「我们都」不在 trie 中，停止；得到0:[0,1]。然后从「们」开始，用同样的方式查询。最终得到的结果是：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1eby14xfnn7j20e1011wef.jpg)

这是一个图的邻接表表示形式，边的权重可以通过 FREQ 得到。只要我们求出图的最大概率路径，便得到了最佳切分方案。有两种方法：

1. DAG的最短路径：Dijkstra算法。我们在大学时的数据结构中已经讲过。（注意我们要求的是最短路径，所以需要将原问题修改一下，w = -log W）
2. 动态规划求最大概率路径。核心代码是这几行：

```python
def calc(sentence,DAG,idx,route):
    N = len(sentence)
    route[N] = (0.0,'')
    for idx in xrange(N-1,-1,-1):
        candidates = [ ( FREQ.get(sentence[idx:x+1],min_freq) + route[x+1][0],x ) for x in DAG[idx] ]
        route[idx] = max(candidates)
```

这个要讲的话也颇费篇幅，简而言之就是从最右边（中文重心在句子尾部）开始，向左，依次计算到达每个节点（字）的最大局部概率，后者表示到达这个节点的最有路径的概率。

至此，基于 DAG 的中文分词算法就介绍完毕了。

预告：最后一篇介绍基于 HMM 的 Viterbi 算法做中文分词。        
       





