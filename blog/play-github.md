title: Play Github
date: 2014-03-19 21:46:14
categories: IT杂谈
tags:
---
今天花时间把 github使用中的一些疑点消灭一下。

###fork & watch & star

到 github 中某人的某个 repo中，会在右上角看到这样的标签：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1eelei341aoj20us01wglm.jpg)

原来一直困惑为啥要有三个，一个 fork 不就得了嘛，其实有三个还是很有必要的。

**fork**: 把该 repo 拷贝到自己的账户下，相当于成为自己的 repo。不同之处是可以通过`pull request`和 original 的那个建立联系。

**watch**: 分为三种级别：not watching,watching,ignore.其实就是用来设置提醒的，比如watching，该 repo 有任何 update 都会收到邮件或 github 中的通知；ignore 就是不接收任何通知。

**star**: 可以理解成「收藏」，这个 repo 的 update 不会出现在 news feed 中。在主页通过「star」标签可以查看自己 star 过的 repo。

一般情况下，遇到好的 repo 想要收藏，就 star。想要自己改改、完善一下，可以 fork。想追踪它的某些 update，可以 watch。

<!--more-->

###pull request

比如 tommy351的 hexo 这个 repo，我 fork 了一下。在我这边修改后，想要告诉 tommy351「我完善了一下，你把我修改后的版本合并到你的 repo 吧」，那么我可以向 tommy351发送一个 pull request。

发送的步骤是：在我这边的 hexo 中，点击右侧的「pull request」，然后「New pull request」，然后查看一下我对 tommy351的 repo 做了哪些改变，确认没错之后，点击「Create pull request」，填写一下说明，即可发送。

tommy351收到我的「pull request」后，如果觉得好，可以 merge，这个就不是我的事了。

###branch

新建一个 repo，默认的branch 是 master。master 作为主分支，要稳定。我们进行迭代开发时，可以新建一个 branch，在这个 branch 中开发，搞定后再合并到 master 中。这样的流程比较合理。

创建： `git branch test`，会新建一个 test 分支，并拷贝 master 的内容到这个分支下。

切换： `git checkout test` 从 master 分支切换到 test 分支。

查看： `git branch` 看看这个 repo 下有哪些分支了。带星号的为当前分支。

删除本地分支： `git branch -d test`

删除远端分支： `git push origin :test` ，注意冒号的意思是删除。

在 test 下的其他操作，如add,commit,push和在 master 下是一样的。

如何合并两个分支呢？

1. 通过`git checkout master`切换到主分支。  
2. 通过`git diff test`查看这两个分支的不同。
3. 确认无误后，通过`git merge test`把 test 合并到 master。

###pull and fetch

这两个操作都是把别处的 repo 拉到这里来，有什么不同嫩？

`git pull` = `git fetch` + `git merge`

比如我目前在我的 hexo 下操作，我想要与 tommy351的 hexo 保持同步。

首先，`git add remote upstream <tommy351的 hexo 地址>`	

如果他五分钟前对hexo这个 repo 做了更改，我现在执行`git fetch upstream` ，并`git diff upstream/master`就可以看到这些变化。 如果我觉得不错，那么通过`git merge upstream/master master`就可以把他做的更改合并到我的 hexo 下。

---
okay，到现在为止，在自己 repo 的 master 下的操作，分支操作，与 original的同步和反馈，以及与他人的社交都会了。以后就要尽量多写代码，并用github 管理代码了。

Have fun!