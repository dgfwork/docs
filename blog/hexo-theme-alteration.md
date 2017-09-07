title: hexo 主题优化
date: 2013-06-26 12:40:43
categories: hexo
tags: hexo theme
---
下载了几个博主修改过的hexo主题源代码，对照自带默认主题light，尝试进行修改。

![](/img/themegai.png)

<!--more-->

修改主题主要涉及的文件是`hexo\themes\light\source\css`和`hexo\themes\light\layout`文件夹下的文件。后者是布局和标签，前者是css定义。对应标签进行修改即可。

我本次修改的部分有这几个：

1. 网页背景、文字颜色等。
 
 这个很简单，找到`hexo\themes\light\source\css\_base\layout.styl`，在body下面增加一条`background-image url('/imgs/noise.png')`，至于背景图片，用自己喜欢的即可。然后在`hexo\themes\light\source\css\_base\variable.styl`中修改color区块中的属性，就可以改变网站不同元素的颜色了。
 
2. 添加drop-shadow效果。
 
 这种效果在前文[《前端之drop-shadow效果》](http://zipperary.com/2013/06/23/box-and-shadow-effect/)中做过详细介绍，这里只是移植过来。需要修改的文件是`hexo\themes\light\source\css\_partial\article.styl`，在`.post-content`下面的平行层级添加一下内容：
 
 ```
   .post-content:before
    content: "";
    position: absolute;
    z-index: -1;
    bottom: 15px;
    left: 10px;
    width: 50%;
    height: 20%;
    -webkit-box-shadow: 0 15px 10px rgba(0, 0, 0, 0.7);
    -moz-box-shadow: 0 15px 10px rgba(0, 0, 0, 0.7);
    box-shadow: 0 15px 15px rgba(0, 0, 0, 0.7);
    -webkit-transform: rotate(-2deg);
    -moz-transform: rotate(-2deg);
    -o-transform: rotate(-2deg);
    transform: rotate(-2deg);
	
  .post-content:after
    content: "";
    position: absolute;
    z-index: -1;
    bottom: 15px;
    left: 10px;
    width: 50%;
    height: 20%;
    -webkit-box-shadow: 0 15px 10px rgba(0, 0, 0, 0.7);
    -moz-box-shadow: 0 15px 10px rgba(0, 0, 0, 0.7);
    box-shadow: 0 15px 15px rgba(0, 0, 0, 0.7);
    -webkit-transform: rotate(-2deg);
    -moz-transform: rotate(-2deg);
    -o-transform: rotate(-2deg);
    transform: rotate(-2deg);
    right: 10px;
    left: auto;
    -webkit-transform: rotate(2deg);
    -moz-transform: rotate(2deg);
    -o-transform: rotate(2deg);
    transform: rotate(2deg);
 ```
 
只做了这点修改，以后看到喜欢的样式再对照修改吧。

另外，已经成功把hexo博客复制一份到wordpress。方法是在wordpress安装这个插件**FeedWordPress**，然后把网站的atom.xml地址填上就可以导入了。还发现一些问题，是wordpress和bae冲突的问题，比如不能在线安装主题和插件，评论异常。问题解决之后会写博客分享。

---

爱打卡-100days-第30天-1111