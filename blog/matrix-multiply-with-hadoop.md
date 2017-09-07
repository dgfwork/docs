title: 理解 MapReduce
date: 2014-01-16 11:05:59
categories: IT杂谈
tags:
---
所谓大数据时代，大数据带来了巨大的好处，也带来了巨大的挑战，其中之一就是大数据的存储和计算。如新浪微博的巨大用户群，若想用矩阵存储用户之间的关系，矩阵的大小是惊人的，不仅传统的存储方式不再适用，在进行一些矩阵运算（如乘法）时更是无能为力了，这时候就需要我们的 MapReduce 上场啦。

MapReduce 是 Google 提出的概念，由于论文中木有提到实现细节，大家只能根据论文所述理论自己实现了。其中最火的是当年雅虎牵头做的开源项目 Hadoop，目前已经得到了非常广泛的应用（如亚马逊、百度）。尽管有这么多顶尖人才在不断优化，但据说 Hadoop 的性能目前还不及 Google 的十分之一。Whatever，大家现在能用的只有 Hadoop 了，而且一般也够用了。

MapReduce 本质是上很简单，就是把原始问题分解成易解的小问题，分发给不同的节点（computer）进行处理，再收集处理后的结果，汇总运算一下，得到最终结果。像极了人工智能中的 And/Or。原理虽简单，MapReduce 的最大贡献还是在于 Scalability,Fault-tolerance 以及对并发和分布式的管理。

在 MapReduce 中，data（可以存储在文件系统，也可数据库） 被主节点计算机（master node） 分配给不同的子节点计算机(worker nodes)进行并行处理，这些 worker nodes 被称为 cluster 或 grid。

下面结合一个矩阵乘法的例子进行说明。

<!--more-->

大矩阵直接存储在文件中不够灵活，而且大矩阵中一般都很稀疏（0元素很多），这样比较浪费。一般的做法是用一个三元组来存储每一个元素。

![](http://ww2.sinaimg.cn/large/5e8cb366jw1ecmdkso46aj202f00jgld.jpg)

表示第 i 行第 j 列的元素为 A。

有如下两个矩阵，我们想求矩阵的乘积：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1ecmdmf49tkj209902xq2w.jpg)

则用上述方法表示两个矩阵：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1ecmdohcuhaj206l0cw0t3.jpg)

矩阵乘法的计算过程很简单，只需要把对应的行列求内积，最后得到一个4行2列的矩阵C。

通过计算过程可以看出，C 中各元素的计算是独立的互不干扰的。这样，我们在Map阶段，就可以把 Cij计算所需要的元素都集中到同一个key（i,j）中，然后，在Reduce阶段就可以从中解析出各个元素来计算。

同时注意到，Aij 会被C 中多个元素的计算用到，所以在 Map 阶段，也要把一个 Aij存储成多个键值对，以备稍后根据不同的键值划分给不同的 reducer 来处理。

处理流程如下：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1ecmdvp19d5j20oz0ergpo.jpg)

其中 shuffle 阶段是 Hadoop 自动完成的；Map 和 Reduce 需要用户自己写代码。上图所示很明晰，不再解释了。

在[wiki](http://en.wikipedia.org/wiki/MapReduce) 中有更加正式的流程定义，同时有另外几个例子，等我理解后再发文分享吧。

欢迎有兴趣者一起交流！

*参考：<http://blog.csdn.net/xyilu/article/details/9066973>*