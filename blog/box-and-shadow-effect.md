title: 前端之drop-shadow效果
date: 2013-06-23 18:03:27
categories: 前端
tags: css
---
今天从[hackernews](https://news.ycombinator.com/)跳入[COMMANDO](https://commando.io/)来看它的『 flatten bootstrap』效果，却被网页简洁、漂亮的UI吸引住了。我对bootstrap已经比较了解，一眼就能看出来这个网站的主页是根据bootstrap主页经过简单修改得到的。一直下拉到网页底部，看到了这个效果：

![](/img/ui1.png)

这种有点立体感的小框，曾在不少网站见到过，一直很喜欢。这次决定认真研究一下效果是什么做出来的。

<!--more-->

比较懒，先在[V2EX](http://www.v2ex.com/t/73328#;)提问，没有得到详细的回答。于是狠心用chrome工具『审查元素』来分析。找到相应模块的标签，找到css文件并根据标签进行查找。将有关的css定义提取出来，做了一个简单的例子进行尝试。终于弄明白这个效果是怎么产生的。

这里先展示一下成品：

![](/img/uidemo.png)

首先新建一个`style.css`文件，用文本编辑器打开，内容如下：

```
/*下面的css定义已经是最精简形式，每一项的更改或删除都会影响最终效果。作为学习，不妨尝试修改小项查看效果，以增加了解。*/
.box {
    background:#fff;
    box-shadow:none;
    border:1px solid #ddd;
    -webkit-border-radius:3px;
    border-radius:3px;
    padding:60px 0;
    margin-top:15px;
    margin-bottom:60px;
}
.drop-shadow {
   position:relative;
}
.drop-shadow:before,
.drop-shadow:after {
   content:"";
   position:absolute;
   z-index:-1;
    bottom:15px;
   left:10px;
   width:50%;
   height:20%;
   -webkit-box-shadow:0 15px 10px rgba(0, 0, 0, 0.7);
   -moz-box-shadow:0 15px 10px rgba(0, 0, 0, 0.7);
   box-shadow:0 15px 15px rgba(0, 0, 0, 0.7);
   -webkit-transform:rotate(-2deg);
   -moz-transform:rotate(-2deg);
   -o-transform:rotate(-2deg);
   transform:rotate(-2deg);
}
.drop-shadow:after{
   right:10px;
   left:auto;
   -webkit-transform:rotate(2deg);
   -moz-transform:rotate(2deg);
   -o-transform:rotate(2deg);
   transform:rotate(2deg);
}
```

css文件做好之后，新建一个html文件做测验。文件名不妨叫`demo.html`，内容如下：

```html
<html >
<head>
 <link rel="stylesheet" href="style.css" type="text/css" />
</head>

<body>
<div class="span12 box drop-shadow">
 <center><h2>This is a demo!</h2></center>
</div>
</body>

</html>
```

注意：此html文件和css文件在同一文件夹下。

保存并打开html文件，就能看到预期效果了。

其中，box的作用是撑起这个『框架』，drop-shadow中的before和after产生框架左右两侧的阴影效果。

---
爱打卡-100days-第27天-1111