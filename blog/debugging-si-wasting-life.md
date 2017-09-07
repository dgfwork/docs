title: Debugging is Wasting Life
date: 2013-08-15 21:13:10
categories:	python
tags:
---
![](http://img12.3lian.com/gaoqing02/02/09/31.jpg)

<!--more-->

今天没控制住自己，结果看了一天的Python。早上看了一个多线程爬虫代码，针对里面出现的不熟悉知识点一一google学习了。之后看豆瓣的那个「python_intro」，介绍的很全面，但由于是ppt转的，未免失详，害得我又google了一番。中午休息的时候突然想到原来打算写的一个爬虫程序，小睡了一会就爬起来写。这个程序会涉及到网络模块、正则表达式、多线程等等，想想就好玩，尤其是需要登录和验证。

开写。嗯，一点点进行的都比较顺利。登录和cookie需要绑定handler，耽误了一点时间，不过也顺利通过了。到了测试和呈现阶段，又遇到了老大难：字符编码问题。这次找到了一个解决方案，使用如下组合拳：

```python
import sys
default_encoding = 'utf-8'
if sys.getdefaultencoding() != default_encoding:
    reload(sys)
    sys.setdefaultencoding(default_encoding)
```

和

```python
response.read().decode('utf-8')
```

这样之后就可以正常呈现了。

但是，到了同一个站点的另一个页面，同样的方法却失效了。简要的代码如下：

```python
import urllib2

url = 'http://mlook.mobi/book/info/6248'
res = urllib2.urlopen(url)
print res.read()
```

试了各种decode和encode依旧乱码。耽误了我老多宝贵的时间，解决不了，每当这个时候就深深感觉到浪费生命，心痛！

把问题贴到了[V2EX](http://www.v2ex.com/t/79217#reply6)。

得到解答后再来更新。


更新：

目前（16号）得到的解答有：

1. `.decode('utf-8').encode('cp936')`
2. `.decode('utf-8').encode('gb18030')`
3. `.decode('utf8').encode(sys.stdout.encoding)`

这三种办法都是试图转换编码，我win下终端有问题，测试直接卡死。

另外就是切换到Linux下操作了。亲测管用。Linux系统的默认编码都是**utf-8**，win下比较邪门。

还有，编码问题是出现在`print`语句上。文件的编码实际上是没有问题的，只有在`print`的时候才会出现编码转换错误，还是说明错误出在终端上，Python是无辜的。

End更新
 

PS:@[itfanr](http://weibo.com/itfan?source=webim)刚刚写了个七牛图床的客户端，很看好七牛这个平台，每个人10G的免费空间，做图床足矣。传送门：<http://itfanr.duapp.com/?p=356>

---

爱打卡-100days-第79天-0111
