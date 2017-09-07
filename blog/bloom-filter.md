title: 认识布隆过滤器
date: 2014-01-24 16:21:33
categories: 机器学习
tags:
---
去年学习爬虫的时候接触过这个概念，得知可以用来 url 查重。不过当时没有涉及这个问题，就搁置下了。前日又看到这个词，正好最近对各种 filter 有些兴趣，索性 break 一下。

所谓 Bloom filter，实际上就是1个数组加上 k 个 hash function组成的一个数据结构.Bloom 是该数据结构的发明人，filter 表明这个数据结构是个过滤器，可以对数据结构中的一部分内容进行操作。

首先给定一个 m 位的 bit 数组，每位取值0或1.初始设置为0.

再给定 k 个hash function，分别把元素a 映射到m 中的 k 个位置。

<!--more-->

**插入元素 a：**如上所述，把映射后的 k 个位置全部置1，已经为1的则保持不变。

**查询元素 a：**同样地做上述映射，得到 k 个位置，只要有非0的，则说明元素 a 不存在。如果 k 个位置都是1，则说明有很大的概率证明 a 存在。为什么说不是百分百？因为k 个位置中的某一个1可能是元素 b 映射过来之后导致的。

**删除元素 a：**No！Never！布隆过滤器中是不能删除元素的。把 a 映射后的 k 个位置置为0可不可以？Nope！因为这些位置不是 a 自己家的，而是全部元素共享的。

在爬虫程序中使用 bloom filter，每访问一个 url，用 bloom filter 看是否存在，if so，说明 url 重复，不需要再访问这个 url 了；if not,说明这个 url 是新的，那么访问该 url，并添加到 bloom filter.

值得指出的是，插入和查询的时间复杂度非常低，速度极快；由于并不存储 url，只是在固定大小的数组里面用组合信息来标志 url，所以空间也非常节省；至于天生存在的错误率，只要m、k、hash functions 设置合适，就能保证错误率在允许的范围内。例如 url 查重中，哪怕存在错误，最多也就多偶尔多访问一次，其弊端几乎可以忽略不计。

bloom filter 简单好用，很值得大家学习了解。另外 Python 中有 lib 可供使用。要让我自己从头设计一个很好的 bloom filter，还不会..

另外，stackoverflow 的一个帖子讨论了一些不常见但很好用的数据结构，推荐给各位： <http://stackoverflow.com/questions/500607/what-are-the-lesser-known-but-useful-data-structures>