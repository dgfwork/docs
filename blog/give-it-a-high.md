title: High 一下
date: 2013-11-19 08:00:00
categories: hexo
tags:
---
今天看酷壳耗子叔的文章时，不经意间又注意到页面右上角的「High一下」功能，玩心顿起，便连High 了好几下。想起中午曾得罪某伙伴，于是想在我的博客放上这个功能，给小伙伴 high 一下作为一个小小的道歉。Google 了一下，介绍此项的网页很少，但在有限的三两个页面里却可以看到其源码，实现起来还是很简单的。

对于 Hexo 用户，可以这样做：

在`Hexo/themes/light/layout/_partial/header.ejs`中的`<ul>`标签内部，增加一对`<li>`标签，并把如下内容拷贝进去：

<!--more-->

```html
<li> <a title="把这个链接拖到你的Chrome收藏夹工具栏中" href='javascript:(function() {
	function c() {
		var e = document.createElement("link");
		e.setAttribute("type", "text/css");
		e.setAttribute("rel", "stylesheet");
		e.setAttribute("href", f);
		e.setAttribute("class", l);
		document.body.appendChild(e)
	}
 
	function h() {
		var e = document.getElementsByClassName(l);
		for (var t = 0; t < e.length; t++) {
			document.body.removeChild(e[t])
		}
	}
 
	function p() {
		var e = document.createElement("div");
		e.setAttribute("class", a);
		document.body.appendChild(e);
		setTimeout(function() {
			document.body.removeChild(e)
		}, 100)
	}
 
	function d(e) {
		return {
			height : e.offsetHeight,
			width : e.offsetWidth
		}
	}
 
	function v(i) {
		var s = d(i);
		return s.height > e && s.height < n && s.width > t && s.width < r
	}
 
	function m(e) {
		var t = e;
		var n = 0;
		while (!!t) {
			n += t.offsetTop;
			t = t.offsetParent
		}
		return n
	}
 
	function g() {
		var e = document.documentElement;
		if (!!window.innerWidth) {
			return window.innerHeight
		} else if (e && !isNaN(e.clientHeight)) {
			return e.clientHeight
		}
		return 0
	}
 
	function y() {
		if (window.pageYOffset) {
			return window.pageYOffset
		}
		return Math.max(document.documentElement.scrollTop, document.body.scrollTop)
	}
 
	function E(e) {
		var t = m(e);
		return t >= w && t <= b + w
	}
 
	function S() {
		var e = document.createElement("audio");
		e.setAttribute("class", l);
		e.src = i;
		e.loop = false;
		e.addEventListener("canplay", function() {
			setTimeout(function() {
				x(k)
			}, 500);
			setTimeout(function() {
				N();
				p();
				for (var e = 0; e < O.length; e++) {
					T(O[e])
				}
			}, 15500)
		}, true);
		e.addEventListener("ended", function() {
			N();
			h()
		}, true);
		e.innerHTML = " <p>If you are reading this, it is because your browser does not support the audio element. We recommend that you get a new browser.</p> <p>";
		document.body.appendChild(e);
		e.play()
	}
 
	function x(e) {
		e.className += " " + s + " " + o
	}
 
	function T(e) {
		e.className += " " + s + " " + u[Math.floor(Math.random() * u.length)]
	}
 
	function N() {
		var e = document.getElementsByClassName(s);
		var t = new RegExp("\\b" + s + "\\b");
		for (var n = 0; n < e.length; ) {
			e[n].className = e[n].className.replace(t, "")
		}
	}
 
	var e = 30;
	var t = 30;
	var n = 350;
	var r = 350;
	var i = "//s3.amazonaws.com/moovweb-marketing/playground/harlem-shake.mp3";
	var s = "mw-harlem_shake_me";
	var o = "im_first";
	var u = ["im_drunk", "im_baked", "im_trippin", "im_blown"];
	var a = "mw-strobe_light";
	var f = "//s3.amazonaws.com/moovweb-marketing/playground/harlem-shake-style.css";
	var l = "mw_added_css";
	var b = g();
	var w = y();
	var C = document.getElementsByTagName("*");
	var k = null;
	for (var L = 0; L < C.length; L++) {
		var A = C[L];
		if (v(A)) {
			if (E(A)) {
				k = A;
				break
			}
		}
	}
	if (A === null) {
		console.warn("Could not find a node of the right size. Please try a different page.");
		return
	}
	c();
	S();
	var O = [];
	for (var L = 0; L < C.length; L++) {
		var A = C[L];
		if (v(A)) {
			O.push(A)
		}
	}
})()    '>High一下</a> </li>
```
代码块的内容不需要再做任何修改。

为了便于直观理解，截图如下：

![](http://ww2.sinaimg.cn/large/5e8cb366jw1eapjmnclddj20ky0h440w.jpg)


可以点击我博客右上角的「High一下」玩一玩。

你也试试吧！