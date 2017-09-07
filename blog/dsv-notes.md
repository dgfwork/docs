title: 数据结构与算法笔记：一
date: 2014-01-04 19:59:17
categories: 机器学习
tags:
---
[数据结构与算法笔记：一 | Zippera's blog](http://zipperary.com/2014/01/04/dsv-notes/)

[数据结构与算法笔记：二 | Zippera's blog](http://zipperary.com/2014/01/06/dsv-notes-2/)

[数据结构与算法笔记：三（大结局） | Zippera's blog](http://zipperary.com/2014/02/23/dsv-notes-3/)

---

这两天在看一个很不错的资源，通过将常见的数据结构和算法可视化为动画或图画的形式，让学习者直观了解这些数据结构的结构形式与常用操作，以及常用算法的代码执行过程，非常受教。

这些知识大部分都有所涉猎或者在课堂上学过，但直观的观察执行过程有助于加深理解。这里简要做些笔记。打算先把内容都看完，然后写代码练习。

网站地址：<http://www.cs.usfca.edu/~galles/visualization/Algorithms.html>

<!--more-->

###Basics

* Stack: Array Implementation： 数组从前往后插入，从后往前删除，用 top 指针指示栈顶（待插入位置）。

* Stack: Linked List Implementation Top： 指针指向非空的链头元素，每次插入都从 top指向的链头位置插入，删除也是从链头。

* Queues: Array Implementation： 数组，head 指向队首元素（在左边），tail 指向队尾元素后面的待插入位置（在右边），插入元素在 tail 处，删除元素在 head 处，两个指针都是从左往右走。

* Queues: Linked List Implementation： head 指向队首元素（在左边），tail 指向队尾元素（在右边），从 tail 插入，从 head 删除。

###Recursion

* Factorial： 求 n 的阶乘。函数if 分支给出分解终止条件；else 分支给出分解函数（自调用）和回溯（整合）的递推式。用 Python 写的。简单、经典。

* Reversing a String： 翻转字符串。过程同上，关键是分解方案。

* N-Queens Problem： n 阶皇后问题：给出 n*n 的棋盘，放上 n 个皇后，使得任意两个横着竖着斜着都不相邻。这个问题之所以用到递归，是因为在试探性（确定性试探，有固定顺序）地放置过程中，如果走入死胡同就需要回溯，倒退到之前的某一步。本质上是图的深度优先搜索策略。Python 代码有点复杂，需要研究并练习。

###Indexing

* Binary Search Trees： 二叉查找树，简单好用。对于每一个节点，左子树任意节点都比他小，右大。中序遍历是一个升序序列。要会插入、删除和查找操作。复杂度为 O(h)。

* AVL Trees (Balanced binary search trees)： 平衡二叉树，首先是二叉查找树，然后满足平衡条件。平衡就是说任意节点的左右子树深度不得超过1，否则就需要旋转变换。这里最重要的知识点就是在插入、删除时，不满足条件时需要进行旋转操作。有三种形式：左旋、右旋、双旋。插入和删除时的旋转是不同的。平衡，保证了树的查找深度可以更小。

* Red-Black Trees： 红黑树，首先也是二叉查找树。然后根据一些规则，保证从跟节点，走到每个叶子节点，经过的黑色节点数相通。这也是保证「平衡」和较小深度的一种方法。  
红黑树五个性质：1. 只有红黑。2. 根黑。 3. 叶（NULL）黑。 4. 红点黑儿子。5. 条条大路同黑数。   
插入过程中，新插入的节点N总是红色的。然后根据其父亲节点P和叔父节点U的情况，进行适当的旋转和变色：P 红 N 红，右右，单旋；P 红 N 红，右左，双旋；P 红 U 红 N 红，黑色下沉一级。  
删除时，先找到替换节点，直接替换，如果不满足结构，则调整。

* Splay Trees： 伸展树，除了二叉查找树的性质，最新访问的节点总是调整到根节点处。这是基于查找的时间和空间局部性原理，可用于 cache。那么，关键之处就在调整了。三种：  
zig-step: p为 root，只需简单旋转。  
zig-zig step：有 g p n，且 p n 都是左或都是右，那么，先旋 g p，再旋 n。  
zig-zag step: 有 g p n，且 p n 不同为左或右，那么先 n p，再 g。

* Open Hash Tables (Closed Addressing)： 同一个位置上，用链表链接多个节点。对于 strings 的 hash，如'hello'，先32位0与'o'的 ascii 求和；结果左移四位，用0补齐；左数11-14位，与'0000'异或；结果与'l'的 ascii 求和...最后的结果，求出10进制，然后hash 到某位置。

* Closed Hash Tables (Open Addressing)： 区别于上面那个，某位置被占后，不可再添加新的元素，应该用再探测法找到其他位置。再探测法包括：线性探测（依次往后找空位），二次探测（1，4，9...）和再 hash（用 hash2）。

* Closed Hash Tables, using buckets： 每连续三个位置为一组（bucket），编号。hash 时，先 hash 到对应的组，如果第一个被占，则用第二个，否则第三个；如果三个都已经被占，则用最后面的额外 overflow 区。

* B Trees： 就是有些书上说的 B-树，英文是 B-tree，是多路查找树，也是平衡树，用于磁盘之类的存储结构。B 树在数据结构一书中是着重学习过的，主要知识点是 m 阶B 树的性质、插入后的分裂操作和删除后的合并操作。

* B+ Trees： 跟 B 树挺像，但有些不同：每层包括所有元素，每层的节点之间有链表链接，有更好的索引性能。在数据结构学习中，这种结构不是重点。