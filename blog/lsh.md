title: An Intuition to Locality Sensitive Hashing
date: 2014-04-01 19:47:00
categories: 机器学习
tags:
---
在 Stackoverflow 的「Machine Learning」标签下随便看，看到一个[How to understand Locality Sensitive Hashing?](http://stackoverflow.com/questions/12952729/how-to-understand-locality-sensitive-hashing)的问题，刚好看视频跟踪时看到有一个 Coherency Sensitive Hashing，莫非两者有不可告人的联系。。索性就学习一下。

先用例子直观地说明一下，请看下图：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1ef0c2v4ps1j20nf0ddt9l.jpg)

上图是一个平面，其中有一个红点和一个黄点，都是二维向量。我们的目的是通过 LSH 方法近似求得这两个点的余弦相似度。

余弦相似度是求向量相似度的一种方法，在图像匹配中很常用。

怎么求呢？

现在，在这个平面上，随记产生 n 条过坐标零点的线，这里 n 取6.

分别给红点和黄点一个 hash 表，实际就是一个二值数组，每个元素取0或1，如左上图所示。白色代表0，黑色代表1.这个 hash 表叫做signature。

先看红点，分别看看这6条线在红点的上方还是下方，并分别标注为0/1，填写在signature 中。需要注意的是，这两个 signature 对应元素代表同一条线。

映射完后，计算这两个 signature 中对应元素不同的个数（hamming distance），比如这里是1个，即最后一个。这有什么意义呢？看图，两个点中只有一条线。由于向量的夹角在[0,PI]之间，有6个线，两个点中只插入了1条，那么两点之间的夹角就可以近似为`PI * 1/6 `。

如图所示：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1ef0ccvna1dj20of0de405.jpg)

<!--more-->

当 n 足够大时，这个估计会非常接近真实值：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1ef0coa709fj20dm02qjrf.jpg)

实际上 LSH 是用采样的方法来近似解析方法求得的真值。至于为什么不直接用解析的方法，我现在还不清楚，可能有些时候解析方法无法求吧。

我觉得这东西跟用蒙特卡洛方法近似求解不规则多边形的面积很像。所谓的 hash，只是一个小 trick 而已。

至于名字「Locality Sensitive Hashing」，应该是说，位置上越接近的向量，其 hash 越相似。

[greeness](http://stackoverflow.com/users/1667256/greeness)提供了一段用 python 写的 demo，很值得看一看：

<script src="https://gist.github.com/greeness/94a3d425009be0f94751.js"></script>

代码很简单，不介绍了。值得注意的是其中的移位运算很巧妙，值得学习。