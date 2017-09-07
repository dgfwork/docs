title: hexo系列教程：（一）hexo介绍
date: 2013-05-28 16:53:13
categories: hexo
tags: [hexo,博客,教程]
---
![](/img/blogshot.png)

###什么是hexo

[hexo](http://zespia.tw/hexo/zh-CN/)是一个基于Node.js的静态博客程序，可以方便的生成静态网页托管在github和Heroku上。作者是来自台湾的[@tommy351](https://github.com/tommy351/hexo)。引用[@tommy351](https://github.com/tommy351/hexo)的话，[hexo](http://zespia.tw/hexo/zh-CN/)：
> 快速、简单且功能强大的 Node.js 博客框架。  
A fast, simple & powerful blog framework, powered by Node.js.

类似于jekyll、Octopress、Wordpress，我们可以用[hexo](http://zespia.tw/hexo/zh-CN/)创建自己的博客，托管到github或Heroku上，绑定自己的域名，用markdown写文章。[本博客](http://zipperary.com)即使用hexo创建并托管在github上。
###为什么要用hexo
<!--more-->
还是引用下作者的话：
>不可思议的快速 ─ 只要一眨眼静态文件即生成完成  
支持 Markdown  
仅需一道指令即可部署到 GitHub Pages 和 Heroku  
已移植 Octopress 插件  
高扩展性、自订性  
兼容于 Windows, Mac & Linux

我再加几条：
  
- 易用。不仅部署简单，平时使用中仅需要`hexo new` `hexo generate` `hexo server` `hexo deploy`四个命令。不像Jekyll需要很多繁琐的`git`命令。
- 轻。文件少、小，易理解，方便自定义。
- 用户多。虽然赶不上Jekyll和Octopress，但遇到什么问题都能搜索到答案，或者找到同样使用hexo的用户进行参考和咨询。

###谁能使用hexo
这是一个免费开源的博客程序，任何人都可以使用和修改。但是不同于wordpress，hexo由于需要使用*Github,Git,Markdown,Node.js*这样的工具，好多插件、widget都需要自己安装、设置。所以适合那些**有一定计算机基础，喜欢折腾**的人。但是，不要恐惧，只要跟着本教程走，就能很方便地让自己的博客"飞起来"。

###怎样搭建hexo博客
正题来了，请期待下一节。

###注意
本系列相关博客均根据hexo**1.1.3**版本，但更高版本也几乎完全适用。各版本所做更新修正，请参考[这里](https://github.com/tommy351/hexo/releases)。
