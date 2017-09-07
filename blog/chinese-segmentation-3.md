title: 中文分词（三）
date: 2013-12-27 22:43:57
categories: 机器学习
tags:
---
* [《中文分词（一）》](http://zipperary.com/2013/12/25/chinese-segmentation/)
* [《中文分词（二）》](http://zipperary.com/2013/12/27/chinese-segmentation-2/)
* [《中文分词（三）》](http://zipperary.com/2013/12/27/chinese-segmentation-3/)

承接上文[《中文分词（二）》](http://zipperary.com/2013/12/27/chinese-segmentation-2/)，本篇是最后一篇，介绍使用基于 HMM 的 Viterbi 算法做中文分词。

###Viterbi 算法

了解 HMM（隐马尔可夫模型）的朋友都知道 HMM 这个模型可以用五元组表示：

```
（states，//状态空间
observations，//观察空间
start_probability，//状态的初始分布
transition_probability，//状态的转移概率矩阵
emission_probability）//状态产生观察的概率
```
<!--more-->

举个例子：

『想象一个乡村诊所。村民有着非常理想化的特性，要么健康要么发烧。他们只有问诊所的医生的才能知道是否发烧。 聪明的医生通过询问病人的感觉诊断他们是否发烧。村民只回答他们感觉正常、头晕或冷。

假设一个病人每天来到诊所并告诉医生他的感觉。医生相信病人的健康状况如同一个离散马尔可夫链。病人的状态有两种“健康”和“发烧”，但医生不能直接观察到，这意味着状态对他是“隐含”的。每天病人会告诉医生自己有以下几种由他的健康状态决定的感觉的一种：正常、冷或头晕。这些是观察结果。 整个系统为一个隐马尔可夫模型(HMM)。

医生知道村民的总体健康状况，还知道发烧和没发烧的病人通常会抱怨什么症状。 换句话说，医生知道隐马尔可夫模型的参数。 』

这里给出该 HMM 的五元组值：

```python
states = ('Healthy', 'Fever')
 
observations = ('normal', 'cold', 'dizzy')
 
start_probability = {'Healthy': 0.6, 'Fever': 0.4}
 
transition_probability = {
   'Healthy' : {'Healthy': 0.7, 'Fever': 0.3},
   'Fever' : {'Healthy': 0.4, 'Fever': 0.6},
   }
 
emission_probability = {
   'Healthy' : {'normal': 0.5, 'cold': 0.4, 'dizzy': 0.1},
   'Fever' : {'normal': 0.1, 'cold': 0.3, 'dizzy': 0.6},
   }
```

上述五元组及其含义，可以用下图形象表示：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1ebynhgilr0j20de0e5js4.jpg)

模型已经建立，那么问题来了：『病人连续三天看医生，医生发现第一天他感觉正常，第二天感觉冷，第三天感觉头晕。 于是医生产生了一个问题：怎样的健康状态序列最能够解释这些观察结果？』

实际上，在我之前的文章[《隐马尔可夫模型三个问题的求解(一)》](http://zipperary.com/2013/10/17/3-problems-in-hmm/)中就做过介绍，刚才提出的那个问题，正是 HMM 三大基本问题之一：根据观察序列，求隐藏状态序列。


**我们总结一下目前的已知条件和待求解问题：**

已知：观察结果 [‘normal’, ‘cold’, ‘dizzy’]  + 如图三个参数。

![](http://ww4.sinaimg.cn/large/5e8cb366jw1ebynmdilkcj20cn04lgm1.jpg)

求：最有可能由状态序列？ （如[‘Healthy’, ‘Healthy’, ‘Fever’]）

求解就用到了 Viterbi 算法，具体的过程请参考52NLP 的[文章](http://www.52nlp.cn/hmm-learn-best-practices-six-viterbi-algorithm-2)，讲的非常好。另外，刚才上面的例子，我借用的是[维基百科](http://zh.wikipedia.org/wiki/%E7%BB%B4%E7%89%B9%E6%AF%94%E7%AE%97%E6%B3%95)。

到此，Viterbi 算法就能把隐藏状态序列求解出来了。

那么，怎样把这厮应用到中文分词呢？

###用 Viterbi 算法做中文分词

一切的算法应用问题，都是把现实问题抽象化，并向算法要解决的问题模型靠拢。

问题模型是什么？HMM。HMM有上面讲过的五个参数，我们要一一对应。

```
（states，//状态空间：{B,E,M,S}，稍后介绍
observations，//观察空间：所有汉字组成的集合。
start_probability，//状态的初始分布
transition_probability，//状态的转移概率矩阵
emission_probability）//状态产生观察的概率
```

**介绍下{B,E,M,S}：**

汉字按照BEMS四个状态来标记，分别代表 Begin End Middle 和 Single，比如：

北京（BE），中华民族（BMME），有意见分歧（SBEBE）

用这四个状态符号依次标记输入句子中的字，便可轻松得到分词方案。 如：

观察序列：我是一个中国人
状态序列：SSBEBME

对于上面的状态序列，根据简单的固定的规则进行组合划分，得到 S/S/BE/BEM/

对应于观察序列：我/是/一个/中国人/

分词任务就完成了。

而后面的三个参数，也可以通过对语料库的统计得到，比如结巴分词中给出的是：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1ebyo4y4cv1j20jo06nq3t.jpg)

已知：观察序列S，初始状态概率prob_start，状态观察发射概率prob_emit，状态转换概率prob_trans。 求状态序列W。

用上面提到的 Viterbi 算法，可以求出 W，也就得到分词方案了。

至此，关于中文分词就介绍完了。有兴趣的同学欢迎交流。


