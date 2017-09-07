title: VIM常用命令
date: 2013-09-03 08:46:19
categories: IT杂谈
tags: vim

---
![](http://ww3.sinaimg.cn/large/5e8cb366jw1e8bd921gscj20j40j4wfy.jpg)

之前写过[《vim使用中的几个问题》](http://zipperary.com/2013/08/24/vim-tips/)这篇文章，介绍了vim使用中几个疑难杂症和一些tips。现在把我收藏的经常使用的VIM命令在这里列举一下。


<!--more-->

###移动光标（普通模式下）

括号匹配：%

同词： #和*    （整个单词，不是字符）

词组： w b  e（词尾）

行内：0 $      ^ g_       (f t下一个bla)

跳行： :22

翻页： ctrl + （fb ud）

首尾： gg G

查找： /word  （n查找下一个）

block： [[和]]

###修改

插入：o O（新行） ；   a（光标后）；i（光标前） ；r（光标处） ； (cw 到词尾)

删除： x X  ； d（删除行） ；   ggdG全部删除

撤销： u 或 ctrl+r

复制：y ；    y$到最后

粘贴：p

大写：gU大写；   gu小写    (选中之后)

替换： :%s/foo/bar

###文件 （命令模式）

退出： w q ！；  ZZ ； :w文件 ； :x（后面加a表示所有文件）

打开： e    （有参数，也可以创建新的）o也可以

另存： saveas

新建： enew    （无参数）

---
爱打卡-100days-第98天-0001
