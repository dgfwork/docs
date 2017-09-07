title: 用Python抓取V2ex网站TopN
date: 2013-08-20 12:01:56
categories: python
tags:
---
![](http://commerce.idaho.gov/assets/content/images/internet-marketing-strategy-traffic1.jpg)

<!--more-->

昨晚在[V2EX](http://www.v2ex.com/)看到有人统计了这个网站回复和收藏数量Top10的帖子。由于站长Livid木有提供排名，这种网友贡献出来的统计结果非常受欢迎。我最近在学python，手痒试一试。

大概想了下方法，就立即着手。一会的功夫就把原型写好了。今天早上又添加了「多线程支持」、「实时进度显示」、「数据保存到文件」等优化功能，现在可以比较方便的使用了。


贴出代码：

<script src="https://gist.github.com/zippera/6276878.js"></script>


线程池大小可以通过`pool`修改。

要统计的页面数量可以通过`last`修改，这是十分必要的，因为开始的页面都是最新更新过的，越往后的帖子上次更新的时间越早，时效性也越差。

Top数量可以通过`topn`修改。

[V2EX](http://www.v2ex.com/)的页数大概4000，很大的数量级，我的电脑还真吃不消。目前只统计了帖子的回复数，也是由于收藏数量的统计消耗太大。等我学了tornado，再把程序布置到BAE，利用百度的超强云服务集群实现更好的动态查询。

> 声明：运行代码爬取网站信息最好选择该网站使用的低谷时间段，以免造成网络拥堵。

---
爱打卡-100days-第84天-0111
