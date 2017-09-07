title: 前端之『折角』效果
date: 2013-06-25 18:21:58
categories: 前端
tags:
---
昨天访问一位Q友的网站，看到一个很nice的效果。如图，上下两个区域交界线的中央处，有一个白色的倒三角，看起来很像上方区域到下放区域的延伸，视觉效果非常不错。我不知道这个效果的学名叫什么，姑且叫做『折角』吧。
![](/img/zhejiaodemo.png)

<!--more-->

发扬『钻头』精神，使用chrome的『审查元素』和『查看源代码』，我把该效果使用的css定义挖掘出来，制作了一个小demo，效果图是这样的：

![](/img/zhejiao.png)

首先新建一个style.css文件，用文本编辑器打开，内容如下：

```
.footer_bottom {
 background:#2c2e2e; 
 min-height:80px;
 } 
.footer_bottom {
 background:url(bg.png);
 }
.footer_bottom h3 {
 color:#FFFFFF;
 }

.frow {
 background:url(row_w.png) 50% 0% no-repeat; 
 padding-top:10px;
 }
```

说明：

* `footer_bottom`的作用是渲染demo中的黑色区域，设定高度、背景图片、区域内文字字体颜色等。

* `frow`的作用就是把我们那个白色的倒三角图片放到合适的位置，`50% 0%`用来控制其位置的横纵坐标。

* [白色三角](https://linost.com/img/row.png)和[黑色背景](https://linost.com/img/bg.png)，都是图片，点击链接查看。文末会给出这个demo的源文件供大家参考。

接下来新建一个`demo.html`文件用来测试效果，内容如下：

```html
<html >
<head>
 <link rel="stylesheet" href="style.css" type="text/css" />
</head>

<body>
<div class="footer_bottom">
  <div class="frow">
     <center><h3>This is a demo!</h3></center>
  </div>
</div>
</body>

</html>
```

好了，这个效果的制作介绍完了，动手试试吧！

PS: demo源文件[在此](http://pan.baidu.com/share/link?shareid=116398762&uk=1661888259)。

---
爱打卡-100days-第29天-0111