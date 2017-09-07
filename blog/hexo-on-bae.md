title: 将hexo博客部署到bae
date: 2013-07-01 07:50:17
categories: hexo
tags: bae
---
我相信很多博主选择使用hexo做为博客程序，一个很重要的原因是可以使用免费、易用的github做为代码托管中心。用过一段时间后我发现，github在国内的速度也不是很理想。于是想到能不能把博客放在百度云BAE上呢，如果成功的话速度应该会有很大的提升。

和新浪的SAE类似，BAE提供web应用的服务器环境，现在支持Python、Java、PHP。不过，这个我们不用关心，因为我们代码是纯静态的，选择哪个环境都是可以的。SAE目前收费了。而BAE，不仅提供无限量的免费存储空间和1G的免费数据库空间，而且速度好像比SAE要快些，操作也十分方便。

就像github，我们可以使用git、svn这样的版本控制工具提交代码。hexo目前默认支持的部署环境为github、heroku，并通过github.js和heroku.js脚本把git命令简化为几个简单的hexo命令，使用起来更加方便高效。按理说我应该类似做一个bae.js，实际上我也尝试了，可惜未果，对其中原理不甚明了。现阶段还是使用原始的git方式提交代码，等以后bae.js成功了会在此更新分享。

下面说一下在bae部署hexo博客的步骤。

<!--more-->

1. [注册bae账号](http://developer.baidu.com/bae)。

 注册账号很简单，点击链接，进入bae主页，按照提示进行操作即可。如果之前没有百度账号，可能需要先行注册。
 
2. 填写开发者资料。

 第一步完成后，在页面右上角可以看到「创建应用」的链接，点击进入后按照提示填写即可。
 
3. 创建应用。

 开发者资料填写好后，右上角的「快速创建应用」就可以用了。按照如下方式填写好，点击「确定」。
 
 ![](/img/bae1.png)
 
4. 托管设置。
 
 点击左侧面板中的「云环境」，进行设置。设置好后点击「确定」，进入「版本管理」。
 
 ![](/img/bae2.png)
 
5. 提交代码。
 
 将hexo目录下的public文件夹打包为public.zip。按照下图方式将代码包上传到bae。完成之后，点击「预览」就可以看到博客了。
 
 ![](/img/bae3.png)
 
6. 同步。
 
 添加文章后怎样提交到bae呢？[这里](http://developer.baidu.com/wiki/index.php?title=docs/cplat/rt/manage/git)有百度给出的详细图文教程。按照教程安装好tortoisegit软件。
 
 以后提交代码时，先使用`hexo generate`命令生成public文件夹，再把public下的文件拷贝到教程中新建的文件夹中去，然后提交该文件夹，这样就能同步到bae了。（提交时，直接commit、push即可，不必先add或delete）
 

这个方法很笨，操作熟练后倒是也很快，不失为一个备选方法。

本博客<http://zipperary.com>依然托管在github，这个<http://me.zipperary.com>在bae上，大家可以感受一下速度是否不同。

---

爱打卡-100days-第34天-1111