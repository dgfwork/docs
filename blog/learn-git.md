title: Learn Git
date: 2013-11-27 14:37:07
categories: IT杂谈
tags:
---
![](http://ww2.sinaimg.cn/large/5e8cb366jw1eazklpf90uj20l80fbgoc.jpg)

Git 几乎是程序员的标配和必备技能，但繁复的命令让人头疼，也吓跑了不少希望学习的小孩。今天看到一个很不错的教程，来自于鼎鼎有名的 CodeSchool，让用户在线跟着教程一步一步边学习边练习。

教程的地址在[这里](http://try.github.io/levels/1/challenges/1)。虽然是全英文的，但几乎可以无障碍理解。

<!--more-->

下面是我的学习总结：

一、基本流程

1. `git init`在本地文件夹建立一个 repo，并做一些初始化配置。
2. `git add [file1]`or`git add .`or`git rm [file2]`在本地文件夹加入或删除文件后，需要用这些命令更新 staged area。后者临时保存用户所提交的更改（如 add/rm），以备下一步的 commit。  
 
 Advice:
 
 `git reset [file1]`可以把 staged area 中所保存的 file1的更新信息删除，恢复之前的样子。
 
3. `git commit -m 'added file1'`把上一步 staged area 中所保存的更改进行整理，更新本地的 repo（准确的说，是本地 repo 的 master 分支），以备后面的 push。
 
 Advice:
 
 `git checkout --[file1]`可以把本地 repo 中 file1的更新还原到之前的状态。
 
4. `git remote add origin https://[服务器端 repo 地址]`添加服务器端的 repo 地址，取名为 origin（可以随便起名），以备稍后提交本地的 repo 到这个服务器端的 repo。
5. `git push -u origin master`把本地 repo 的 master 分支提交到刚才添加的那个服务器端分支 origin。`-u`表示记住后面的参数，以后 push 的时候直接用`git push`命令即可。

至此，本地的 repo 已提交到服务器端。

二、分支

1. `git branch [newbranch]`上面说过，repo 里面默认的是 master 分支，这个命令可以创建其他分支。 `-d`可以用来删除某个分支。 这个分支可以用来修复 master 分支中代码的 bug，然后在 merge 到 master。
2. `git checkout [newbranch]`切换到这个新的分支，然后就可以在这个分支下写代码改代码了。
3. `git checkout master`  
 `git merge [newbranch]`切换回 master 分支，然后把刚才新分支对代码所做的更改 merge 进来。
 
上述操作流程是多人合作写代码要使用的。各自先在小分支中修改，然后 merge 到主分支。 

三、 状态跟踪

1. `git status` 查看当前状态。
2. `git log`查看更改记录。
3. `git diff`查看更改前后的对比。

上述三个可以随时用来查看状态，三个的区别，我还不是太懂。

四、资料推荐

1. `git`在命令行中使用这个命令可以获取相关的说明和帮助。
2. [Git - Reference](http://git-scm.com/docs)参考手册性质的，可以随时用来查阅；还有CheatSheet可供下载，福利啊。
3. [Pro Git](http://git-scm.com/book) 教程，全英文。想阅读中文版本，Come [here](http://git-scm.com/book/zh)。
4. [GitHub Help](https://help.github.com/)Github提供，相当于一个 FAQs。
5. [图解Git](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)帮助你深刻理解这些命令，有图有真相。
6. [寫給大學生的程式技能](http://blog.xdite.net/posts/2013/11/22/opensource-cheatsheets?utm_campaign=Manong_Weekly_Issue_11&utm_medium=EDM&utm_source=Manong_Weekly)今天看到的，一步步指导学习使用 github，非常 practical，via this, you can learn git && github together.
7. If you are eager to learn more,click [here](https://www.google.com/cse/publicurl?cx=014607101523563003145:y4ccw7deyqg).Besides,you can google other topics such as `Python` in my customized Google.