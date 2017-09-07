title: hexo系列教程：（二）搭建hexo博客
date: 2013-05-28 17:28:53
categories: hexo
tags: [hexo,博客,教程]
---
[上一节](http://zipperary.com/2013/05/28/hexo-guide-1/#more)对hexo进行了简单介绍，本节来讲讲怎么搭建hexo博客。

**注意**：本节教程只针对Windows用户，Linux和Mac用户请移步[hexo安装](http://zespia.tw/hexo/zh-CN/docs/install.html)。

###安装Git
下载 [msysgit](http://code.google.com/p/msysgit/) 并执行即可完成安装。
###安装Node.js
在 Windows 环境下安装 Node.js 非常简单，仅须[下载](http://nodejs.org/)安装文件并执行即可完成安装。
###安装hexo
利用 npm 命令即可安装。（在任意位置点击鼠标右键，选择*Git bash*）
```
npm install -g hexo
```
###创建hexo文件夹
安装完成后，在你喜爱的文件夹下（如`H:\hexo`），执行以下指令(在`H:\hexo`内点击鼠标右键，选择*Git bash*)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。
```
hexo init 
```
###本地查看
<!--more-->
现在我们已经搭建起本地的hexo博客了，执行以下命令(在`H:\hexo`)，然后到浏览器输入`localhost:4000`看看。
```
hexo generate
hexo server
```
好了，至此，本地博客已经搭建起来了，只是本地哦，别人看不到的。下面，我们要部署到Github。
###注册Github账号
已有账号可以跳过，没有的，请[在此](https://github.com/signup/free)进行注册，很简单，这里就不介绍了。
![](/img/repo.png)
###创建repository
在自己[Github](https://github.com/)主页右下角，创建一个新的repository。比如我的[Github](https://github.com/)账号是[zippera](https://github.com/zippera)，那么我应该创建的repository名字应该是`zippera.github.io`。

![](http://ww2.sinaimg.cn/large/5e8cb366jw1ea6opuis78j20au01qq2t.jpg)

###部署
编辑`_config.yml`(在`H:\hexo`下)。你在部署时，要把下面的`zippera`都换成你的账号名。
```
deploy:
  type: github
  repository: https://github.com/zippera/zippera.github.io.git
  branch: master
```
执行下列指令即可完成部署。
```
hexo generate
hexo deploy
```
**注意：**有些新用户需要设置 ssh，否则上述命令会失败。ssh 的介绍和设置方法请看[官方教程](https://help.github.com/articles/generating-ssh-keys)，不用担心，很简单。

**记住：**每次修改本地文件后，需要`hexo generate`才能保存。每次使用命令时，都要在`H:\hexo`目录下。

Okay,我们的博客已经完全搭建起来了，在浏览器访问`zippera.github.io`就能看到你的成就了！

###bugs

1. 有网友反应右键菜单中没有`git bash`选项，可以进入开始菜单找到`git bash`，然后通过`cd`进入相应目录执行命令。
2. 在github部署完成之后，马上访问可能出现404错误，这是正常的，（最多）等待十分钟左右就可以访问了。如果还不行，那很可能是 github 发送给你的验证邮件你没有打开看，据多方反映，验证后就没问题了。
3. 如果在`hexo d`之后出现`fatal: 'username.github.io' does not appear to be a git repository`，一是检查 repo 的名字是否合乎规范、是否含有大写字母、config.yml 中的 deploy 配置是否正确，二是把 git bash 关掉，重新打开再执行命令。
4. 有的同学可能不是 IT 界的，或者对shell 命令不太了解。在要求输入密码时，你输入之后密码是不显示的，这是为了安全，并非是你没输上。
5. 出现乱码的，不要使用 windows 中的「记事本」打开并编辑文件，推荐使用 sublime text，很简单。如果已经在「记事本」中编辑过，需要使用 sublime text 转码为「utf8」。
6. 安装 hexo 时卡在那儿不动，很可能是网络不给力，能全局 break wall 就好了。
7. 遇到什么其他的问题，不妨删除.deploy 和db.json 再重新生成试一试。

###tips

hexo现在支持更加简单的命令格式了，比如：

`hexo g` == `hexo generate`

`hexo d` == `hexo deploy`

`hexo s` == `hexo server`

`hexo n` == `hexo new`

在下一节中，我们会介绍如何配置自己的网站，如何撰写和发表文章。

---
爱打卡-100days-第1天-0111