title: hexo系列教程：（四）hexo博客的优化技巧
date: 2013-05-30 07:28:53
categories: hexo
tags: [hexo,博客,教程]
---
[上一节](http://zipperary.com/2013/05/28/hexo-guide-3/)中我们已经学会了用hexo发布博客，这里再介绍一些小技巧对博客站点进行优化，实现更加丰富的功能。

###添加“多说”评论

hexo默认使用国外比较流行的disqus，不过，按照“因地制宜”的原则，我们修改为国内用的多又好用的“多说”评论系统。步骤非常简单：

1. 在[多说](http://duoshuo.com/)进行注册，获得通用代码。
2. 将通用代码粘贴到`themes\light\layout\_partial\comment.ejs`里面，如下：
```html
<% if ( page.comments){ %>
<section id="comment">
通用代码
</section>
<% } %>
```

*很多网友反映自己使用的非 light 主题中找不到相应的文件。我的这些修改都是在 light主题中，其他主题没有了解过，各位只好自己探索了。*

###添加『页面导航』

在刚才添加「多说」评论的文件中，加入一段代码，如下：

```html
<% if ( page.comments){ %>

 <nav id="pagination" >
    <% if (page.prev) { %>
    <a href="<%- config.root %><%- page.prev.path %>" class="alignleft prev" ><%= __('prev') %></a>
    <% } %>
    <% if (page.next) { %>
    <a href="<%- config.root %><%- page.next.path %>" class="alignright next" ><%= __('next') %></a>
    <% } %>
    <div class="clearfix"></div>
</nav>

<section id="comment">

```


###添加“百度分享”

到[百度分享](http://share.baidu.com/code)获得代码，在`themes/light/layout/_partial/article.ejs`中，将`<%-partial('post/share')%>`删掉，替换为百度分享的代码。
<!--more-->
###添加小图标

在`themes/light/layout/_partial/head.ejs`里将`<link href="<%- config.root %>favicon.png" rel="icon">`替换为`<link href="<%- config.root %>favicon.ico" rel="icon" type="image/x-ico">`。将favicon.ico图标文件放在source目录下。制作图标的网站，<http://www.faviconer.com>。

###添加分类、标签云widget

很简单，在`themes/light/_config.yml`中，添加如下：
```
widgets:
- category
- tagcloud
```

###添加友情链接widget

1. 在`themes/light/layout/_widget`中新建名为`blogroll.ejs`的文件，编辑内容如下：
```html
<div class="widget tag">
<h3 class="title">友情链接</h3>
<ul class="entry">
<li><a href="http://zipperary.com/" title="Zippera's Blog">Zippera</a></li>
</ul>
</div>
```

2. 在`themes/light/_config.yml`中，添加如下：
```
widgets:
- blogroll
```

###生成post时默认生成categories配置项

在`scaffolds/post.md`中，添加一行`categories:`。同理可应用在`page.md`和`photo.md`。

###添加新浪微博widget(微博秀)

1. 去[新浪微博开放平台](http://open.weibo.com/widget/weibotopic.php)设置和生成微博秀代码。
2. 在`themes/light/layout/_widget`中新建名为`weibo.ejs`的文件，将刚才的代码直接保存到这里。
3. 在`themes/light/_config.yml`中，添加如下：
```
widgets:
- weibo
```

###导航栏添加"关于"

1. `hexo new page "about"`
2. 到`source/about/index.md`编辑内容。
3. 在`themes/light/_config.yml`中，添加如下：
```
menu:
  关于: /about
```

###主页文章显示摘要

编辑md文件的时候，在要作为摘要的文字后面添加`<!--more-->`即可。

优化是无止境的，今天先写这些。

---
爱打卡-100days-第3天-1111