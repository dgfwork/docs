title: 中文分词之词性标注与关键词提取
date: 2014-01-26 14:02:20
categories: 机器学习
tags:
---
之前[发文](http://zipperary.com/2013/12/27/chinese-segmentation-3/)剖析了「结巴分词」中用「DAG」和「Viterbi」算法进行中文分词的两个方案。有了前面的基础，这里再来讨论词性标注（POS）与关键词提取。

###词性标注

如图，在 DAG分词时所用的 dict 里面含有词汇、词频和词性三个信息。所以，最简单的情况下，只需要在分词时查询 dict 记录下每个词的词性即可。

![](http://ww4.sinaimg.cn/large/5e8cb366jw1eby0f7c9a4j20v50h5ta6.jpg)

对于 dict 中没有给出 pos 信息，或者采用 Viterbi 算法对 OOV 做分词时，需要采用另外一种方法。这种方法本质上很简单，也是采用 Viterbi 算法，只是 model 稍微做些改变。

<!--more-->

之前的文章介绍用 Viterbi 做中文分词时，我们指出观察空间为所有中文字组成的集合，状态空间为{B,E,M,S}，并给出了三个先验的概率表：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1ebyo4y4cv1j20jo06nq3t.jpg)

这样，Viterbi 算法所基于的 HMM 模型就构建完全了，只需要执行 Viterbi 算法，就能计算出最可能的状态序列，并据此得到分词方案。

针对词性标注，我们对 HMM 模型稍作修改。观察空间不变；状态空间在前述基础上融入词性；初始状态分布表、状态转移概率表、发射概率表也做相应修改。如图所示：

![初始状态分布表](http://ww2.sinaimg.cn/large/5e8cb366jw1ecwx8xf48pj20pd0bhq4c.jpg)

![状态转移概率表](http://ww4.sinaimg.cn/large/5e8cb366jw1ecwxacbb66j20pf0bgtak.jpg)

![发射概率表](http://ww2.sinaimg.cn/large/5e8cb366jw1ecwxbiko18j20b106rdgw.jpg)

给定了新的 HMM 模型，再应用 Viterbi 算法，就能得到最可能的状态序列了。然后怎么做呢？

对上面得到的状态序列，从左到右扫描：如果是 E，则此时的 pos 即为 E 对应的 pos，此时的 word 为上一个 B 到该 E 之间的字组；如果是 S，则该字单独作为词，其对应的 pos 就是该词的 pos。在此过程中，分词和词性标注是同时完成的。

###关键词提取

在[《中文分词（二）》](http://zipperary.com/2013/12/27/chinese-segmentation-2/)中我提到过，生成 trie 时，顺便把 lfreq 转为 FREQ：

```python
FREQ = dict([(k,log(float(v)/total)) for k,v in FREQ.iteritems()]) #normalize
```
说道是为了「计算TF-IDF，以实现关键词提取的功能」。既然已经计算好了，要实现关键词提取就手到擒来了。在分词完成之后，对每个词汇，查询对应的TF-IDF值，并取出值最高的 k 个词汇即可。

TF-IDF的概念很简单，可参考阮一峰的[《TF-IDF与余弦相似性的应用（一）：自动提取关键词》](http://www.ruanyifeng.com/blog/2013/03/tf-idf.html)。

###多说一句

上述分词、词性标注和关键词提取，方法原理都很简单，在使用时，最关键的是 Model 的建立，如 dict.txt 和 HMM 模型中的那些表。这些东西可以通过语言学家们提供的现成的语料库获得，也可以自己通过现成的工具训练得到。算法是死的，个人改进的空间不太大，而先验数据是活的，大有提升的余地。