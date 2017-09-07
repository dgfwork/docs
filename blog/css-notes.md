title: CSS学习笔记 
date: 2013-08-17 00:19:50
categories: 前端
tags: CSS
---
![](http://images.51cto.com/files/uploadimg/20120913/0953270.png)

之前做网站自己搞前端，在**w3cschool**杂乱地把html，css，jquery，ajax的教程学习了一遍，然后用刚刚诞生不久的Bootstrap作为前端框架，算来我属于BS最早的一批用户了:)

 最近学python之外，很想把CSS、jquery学的更好一点。把原来做过的笔记复习了一下，然后打开Bootstrap的**Bootstrap.css**，一行一行地看，不会的一一Google，在旁边做注释。不过这个工程量太大了，其实很多是重复的，不必要全部都看。
 
 看过一些后我就去改博客的样式。Hexo用的是stylus，而不是直接用CSS，所以先简单学了下stylus的语法，很简单，只是把CSS语法简化了，[官网首页](http://learnboost.github.io/stylus/)写的很明白。在学习Bootstrap的CSS文件时，主要用到了w3cschool的[CSS参考手册](http://www.w3school.com.cn/css/css_reference.asp)，「Ctrl + F」找到后点进去会有详实的解释和生动的例子，很好用。
 
废话少说，这篇博客主要是把目前的笔记贴上来。

<!--more-->

###简介

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明。

选择器通常是您需要改变样式的 HTML 元素。每条声明由一个属性和一个值组成。属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。

###引用CSS

1. **外部样式表** `<link rel="stylesheet" type="text/css" href="mystyle.css" />`

2. **内部样式表** `<style type="text/css">css代码</style>`

3. **内联样式表** 写在html标签内。

这里需要注意的是，如果一个样式在三个里面都有，那么优先级依次提高，也就是说最终会使用3里面的这个。

###常用规则

* 子元素继承后，可override。
* 上下文选择器（所有后代） (contextual selectors) `li strong {...}`
* 子元素选择器（直接后代）`h1 > strong`
* 相邻兄弟选择器 `h1 + p`
* id派生 `#sidebar p`
* 类选择器 `.center`  也可派生
* 属性选择器 `[title]{...}`
* 属性和值选择器 `[title=W3School]` 另外，`[title~=hello]`值里面包含hello的`[lang|=en]`值中有连字符

###浏览器私有属性

不同浏览器对CSS的支持不尽相同，有些属性只有特定的浏览器才支持。

-moz、-ms、-webkit 、-o

分别为firefox、IE、chrome及safari、opera。

###注意事项

1. **一切皆为框**（可通过display改变）。div、h1 或 p元素常常被称为块级元素。这意味着这些元素显示为一块内容，即“块框”。与之相反，span 和 strong 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。

2. **定位机制**。有三种基本的定位机制：普通流、浮动和绝对定位。除非专门指定，否则所有框都在普通流中定位。（按照标签出现的位置）  
相对定位：相对于原位置进行移动。原来的位置仍然占据。  
绝对定位：是“相对于”最近的已定位祖先元素，如果不存在已定位的祖先元素，那么“相对于”最初的包含块。

3. **颜色**。当使用RGB百分比时，即使当值为0时也要写百分比符号。

4. **注释**。用`/*...*/`

5. **通配符**。可以使用星号作为通配符。

###几个高级应用举例

1. `text-shadow: 0 1px 0 rgba(255,255,255,.1);`
 
 这个可以用来设置字体的阴影效果。各值的含义分别为：横向偏移、纵向偏移、阴影宽度、阴影颜色。

2. `transition:width 2s;`
 
 样式过渡效果，第一个值是需要过渡的css selector，第二个是过渡的速度（时间）。比如鼠标放在一个元素上，该元素便开始过渡到另一种样式。

3. `background-image: -webkit-linear-gradient(left, rgba(0,0,0,0), rgba(0,0,0,.1));`
 
 颜色过渡效果。这里用webkit指明是chrome或safari浏览器才有的私有属性。并且通过linear指明是线性过渡。各值的意义分别为：过渡方向（从左到右）、开始颜色、停止颜色。


CSS的规则很简单，但小知识点很多，企图一下学完并记住是不现实的。最好记住上面这些基本的规则，用好上述的手册，遇到好看的样式时就分析学习一下，写个例子应用试试，日积月累才能学好。

---

爱打卡-100days-第81天-1111
