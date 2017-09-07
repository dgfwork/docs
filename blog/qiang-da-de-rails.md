title: 强大的rails
date: 2013-08-30 19:20:17
categories: Ruby
tags: rails
---
![](http://ww1.sinaimg.cn/large/5e8cb366jw1e85o6gmq6cj211y0kq0wa.jpg)

Ruby的入门，在[Ruby走起](http://zipperary.com/2013/08/28/ruby-on/)一文之前就结束了。这两天各种闲杂之事，断断续续的学习了一些rails的知识。主要参考了地瓜哥的[《Agile Web Development with Rails》抄书笔记](http://www.diguage.com/archives/tag/ruby)系列文章。rails的入门教程，首推《Agile Web Development with Rails》这本书。这个系列的博客，是地瓜哥学习这本书的过程，不仅把书中的内容清晰的展示在博客中，同时把他自己遇到过的问题、解决的办法和发现的好资料都分享在这里，干货值非常高。rails的强大之处在于，只需要几个简单的命令，一个网站所需要的结构和文件都会自动创建，立即可以使用。如果需要，仅需修改默认值即可。这里概括一下基本的流程。

<!--more-->

###安装

尽管前辈们都列出了`mac > linux >> windows`，对于我来说，mac木有，linux折腾不起，还是win吧。windows用户有福了，安装特别简单。

**下载并安装[Rails Installer](http://railsinstaller.org/)。**

这一步会安装好以下组件：
Ruby
Rails
Bundler
Git
Sqlite
TinyTDS
SQLServerSupport 
DevKit

安装好之后，进入终端，使用`ruby -v`和`rails -v`查看版本号。

值得一提的是，对于中国用户，最好修改gem源，该用淘宝提供的镜像，速度刷刷的。

在终端依次输入：
```
gem sources -l
gem sources --remove https://rubygems.org/ 
gem sources -a http://ruby.taobao.org/
```

最后再`gem sources -l`，确保目前的镜像是淘宝的。


###开发项目

从头开发一个项目，大概有这么几个流程：

1. `rails new demo` 新建一个项目，会在当前目录下生成项目的文件夹。然后就可以`rails s`运行服务器，打开终端提示的地址查看web。*后面的几个命令都需要切换到demo目录下执行*

2. `rails generate scaffold Product title:string description:text` 这个命令非常强大。我们知道，rails是MVC架构。这个命令会生成Product这个controller、相应的view、model，以及product数据表，并自动将这些组件进行关联。也就是说，生成这个数据表，以及跟数据表相关的各种操作功能。

3. `rake db:migrate` rake命令有点像linux中的make，它会自动跟踪并查找没有执行过的迁移脚本，并执行迁移工作。对于我们这个例子，它的工作就是具体生成数据库及product表。

4. `rake test` 自动执行测试工作，并报告测试结果。

5. `rails s` 开启服务器，打开<http://localhost:3000>。你看到的绝对比你预想的多，这就是rails的强大。


以上列举了rails最常用的命令和整体的流程。具体开发过程中的技巧细节，需要跟着教程一点点的学习和练习。我在学习过程中也会及时分享，请关注这个catagory。

顺便多说一句：Sublime Text真是太太太好用了！

---
爱打卡-100days-第94天-0011
