title: 把flickr相册嵌入网页
date: 2013-07-09 10:22:35
categories: hexo
tags: flickr
---
![](/img/flickr.png)

flickr是雅虎旗下的图片存储与分享服务，注册即赠送1T的免费存储空间，足够这辈子用了。flickr会无损保存我们的照片，提供各种滤镜渲染效果。同时，flickr的图片展示方式也非常的方便和舒适，幻灯片效果尤为漂亮。本文介绍一种方法，把自己的图集在博客页面上进行展示。效果如上图所示。

<!--more-->

方法很简单，代码如下：

```html
<iframe frameborder="0" width="100%" height="500" scrolling="no" src="http://www.flickr.com/slideShow/index.gne?set_id=#####"></iframe> 
```

其中，`frameborder`是边框；`width`和`height`分别设置宽度和高度，可以是绝对尺寸，也可以是百分比；`scrolling`是滚动与否；最后的`src`是相册集的链接，必须使用这种格式，set_id是相册集的id，可以在自己相册集的URL中看到。

我们可以单独建立一个页面用来展示自己的图册，方法可参考[《hexo系列教程：（四）hexo博客的优化技巧》](http://zipperary.com/2013/05/30/hexo-guide-4/)中的「导航栏添加"关于"」。只要将上述代码填入正文即可。

---

####今日推荐：为知笔记

可以完美导入Evernote中的笔记、分类和标签。相较于Evernote，为知笔记速度更加流畅、使用体验更加人性化，有各种各样的插件方便拓展功能，尤其是支持markdown。已经用了一周了，很好用，谁用谁知道！

传送门：<http://www.wiz.cn/>

---
爱打卡-100days-第42天-0111