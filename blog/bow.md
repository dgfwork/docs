title: Bag of Words
date: 2013-12-10 09:11:38
categories: 机器学习
tags:
---
Bag of Words，即词袋模型，是对样本数据的一种表示方法，主要应用在 NLP(自然语言处理)和 IR(信息检索)领域，近年也开始在 CV（计算机视觉）发挥作用。

###模型假设

该模型在表示样本数据时，通过如下假设对模型进行简化：一个文本或文档可以看作一袋子的单词，而不考虑其语法和词序关系，每个词都是独立的（有点 unigram 的赶脚）。

###示例

有这样两个简单的文本文档：

```
John likes to watch movies. Mary likes too.
```

```
John also likes to watch football games.
```

对上述两个文档构造词典：

```
{
    "John": 1,
    "likes": 2,
    "to": 3,
    "watch": 4,
    "movies": 5,
    "also": 6,
    "football": 7,
    "games": 8,
    "Mary": 9,
    "too": 10
}
```

词典中共有10个词项，每个词项后面是序号。那么，我们可以用一个向量表示一个文本文档：

```
[1, 2, 1, 1, 1, 0, 0, 0, 1, 1]
[1, 1, 1, 1, 0, 1, 1, 1, 0, 0]
```
上面的这个矩阵图形式的表示，就是词袋模型了，其中每个分量表示该词项在该文档中的出现次数。可以看到，词序的信息已经丢失，每个文档只看做一些单独词项的集合。

顺便说一下，矩阵图中的每一项，不仅可以用词典频数表示，一个更常用的方法是用[tf-idf](http://en.wikipedia.org/wiki/Tf%E2%80%93idf)表示词项的权重。

<!--more-->

###应用举例

一个常见的应用是基于此模型做邮件过滤，也就是对邮件分类为 Spam(垃圾邮件)和 Ham(保留邮件)。我们知道垃圾邮件中经常会出现的一些词，比如"stock", "Viagra",  "buy"，那么就可以利用这个特点进行分类了。具体的分类方法是使用[贝叶斯规则](http://en.wikipedia.org/wiki/Bayesian_probability)。

另外，还可以用于图片的分类：

一个图片由若干个 local features（或叫做 patchs）表示，用 Kmeans 方法把相似的 patchs 聚类，每个聚类找出一个代表性的 patch，叫做 codeword，类比于 NLP 中的 word；同样的，图片就类比文本文档。用每个图片得到的 codeword 构建词典，叫做 codebook，类比 NLP 中的词典。这样，每个图片就可以用视觉词袋模型，以同维向量的形式表示出来。之后便可以使用 svm 等方法进行分类。

###后记

BOW 是一个非常常见的概念，名字略古怪，实际上很贴切，也很简单。上面我大概翻译了一下Wikipedia中的解释，有兴趣的同学可以点击原文查看，英文的表达似乎更容易理解。对 CV 中 BOW 感兴趣的同学，可以点击后面的那个链接。

参考资料：

* [Bag-of-words model - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/Bag-of-words_model)
* [Bag-of-words model in computer vision - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/Bag-of-words_model_in_computer_vision)