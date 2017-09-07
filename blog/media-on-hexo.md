title: 怎样在博文中嵌入图片、音乐、视频？
date: 2013-06-27 11:32:27
categories: hexo
tags: 
---
到目前为止，我的博客中几乎清一色的文本，偶尔夹杂图片。今天在[SinChang的博客](http://sinchang.github.io/2013/06/26/music/)中看到博客中嵌入了音乐，于是想了解一下怎样在博文中嵌入音乐、视频、flash等多媒体文件。

实际上，在hexo中，markdown支持html标签，md文件解析为html时原有的html部分会保留。有基于此，我们只要在文中插入符合html规范的代码即可。下面举例说明。

###图片

代码：

```
![](http://ww2.sinaimg.cn/large/5e8cb366jw1e62o63tkv3j20dh078q5a.jpg)
```

效果：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1e62o63tkv3j20dh078q5a.jpg)

<!--more-->

###音乐

以『虾米音乐』为例，歌曲页面有个『转帖』选项，将html代码或javascript代码复制到文中即可。

代码：

```html
<embed src="http://www.xiami.com/widget/0_3515679/singlePlayer.swf" type="application/x-shockwave-flash" width="257" height="33" wmode="transparent"></embed>
```

效果：

<embed src="http://www.xiami.com/widget/0_3515679/singlePlayer.swf" type="application/x-shockwave-flash" width="257" height="33" wmode="transparent"></embed>

###视频

嵌入视频的方法和音乐类似，视频网站每个视频页面都会有一个『分享』或『转帖』按钮，点击可以查看代码。

代码：

```html
<iframe height=498 width=510 src="http://player.youku.com/embed/XMjI2MjU3MDMy" frameborder=0 allowfullscreen></iframe>
```

效果：

<iframe height=498 width=510 src="http://player.youku.com/embed/XMjI2MjU3MDMy" frameborder=0 allowfullscreen></iframe>

###万能

对于有些音乐、视频找不到『转帖』按钮的，可以查看源代码，找到相应的代码块贴在文中。若找不到，说明该文件的确不能放在自己文中了。

---

爱打卡-100days-第31天-0111
