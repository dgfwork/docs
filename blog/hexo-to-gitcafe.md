title: 托管博客到gitcafe
date: 2013-11-23 13:30:47
categories: hexo
tags:
---
前几天帮同学弄 hexo 博客，她的电脑是 windows，不支持 rsync 功能，只能托管到 github。但是代码提交上去之后，访问网址时总不显示最新更新的内容，尝试了所有能够想到的办法，狠命折腾了一番，仍无果（在论坛看到消息，github 最近被黑了）。昨日得朋友指点，gitcafe 好像也可以免费托管静态博客。今日 google 了一下，果然可以用。另外，刚刚知道这家网站是国内的，访问速度刷刷刷，比 github 快多了。

首先，在[gitcafe](http://gitcafe.com/signup?invited_by=zippera)注册并创建项目。与 github 类似，项目名和用户名要一致。(注意：要创建「公开项目」而不是「私有项目」)

![](http://ww2.sinaimg.cn/large/5e8cb366jw1eauweqii0lj209k03z3yl.jpg)

<!--more-->

在[SSH公钥管理](https://gitcafe.com/account/public_keys)中，填写电脑上保存的公钥。从未设置过 SSH 的用户，可参考[这里](https://help.github.com/articles/generating-ssh-keys)。

去`hexo\_config.yml`添加如下代码（用户名和项目名替换为自己的）：

```
deploy:
  type: github
  repository: git@gitcafe.com:zippera/zippera.git
  branch: gitcafe-pages
```
保存之后，用`hexo d`上传到 gitcafe 即可。现在就可以通过<http://zippera.gitcafe.com/>进行访问了。

如果需要绑定私有域名，可以参考[这里](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9)的说明。

比较推荐 windows 用户使用 gitcafe，速度很不错。

---
###Mac tricks:更改文件的默认打开方式

在 Finder 中选中某文件，使用快捷键`⌘ + i`打开文件简介，在「打开方式」中选择相应的程序，然后选择「全部更改」即可。