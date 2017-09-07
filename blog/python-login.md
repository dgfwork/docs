title: 用Python模拟浏览器登录
date: 2013-08-16 19:03:50
categories: python
tags: 爬虫
---
![](http://www.adafruit.com/adablog/wp-content/uploads/2012/03/index-18.jpg)

我的博客中曾经贴过几个爬虫程序的[代码](http://zipperary.com/categories/python/)，用来批量下载图片非常方便。这样的爬虫实现起来比较简单。而有些网站需要用户登录之后才可以下载文件，之前的方法就办不到了。今天就说说用Python模拟浏览器的登录过程，为之后的登录下载做好准备。

登录的情况，需要额外用到的一个模块是**cookielib**，用来记住登录成功之后保存到本地的cookie，方便在网站的各个页面之间穿越。

<!--more-->

先上代码示例：

```python
#encoding=utf8
import urllib
import urllib2
import cookielib

###登录页的url
lgurl = 'http://mlook.mobi/member/login'

###用cookielib模块创建一个对象，再用urlllib2模块创建一个cookie的handler
cookie = cookielib.CookieJar()
cookie_handler = urllib2.HTTPCookieProcessor(cookie)

###有些网站反爬虫，这里用headers把程序伪装成浏览器
hds = { 'User-Agent' : 'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/28.0.1500.72 Safari/537.36' }  

###登录需要提交的表单
pstdata = {'formhash':'', #填入formhash
	'person[login]':'', #填入网站的用户名
	'person[password]':'', #填入网站密码
	}

dt = urllib.urlencode(pstdata) #表单数据编码成url识别的格式
req = urllib2.Request(url = lgurl,data = dt,headers = hds) #伪装成浏览器，访问该页面，并POST表单数据，这里并没有实际访问，只是创建了一个有该功能的对象
opener = urllib2.build_opener(cookie_handler) #绑定handler，创建一个自定义的opener
response = opener.open(req)#请求网页，返回句柄
page = response.read()#读取并返回网页内容

print page #打印到终端显示
```

说明一下：

1. 我这里就不提供用户名密码了。关于需要提交的表单数据，chrome用户可以`F12 -> Network -> 填好账号密码并登录 -> 在Network找到POST...`，请看截图。
 
 ![](http://ww4.sinaimg.cn/large/5e8cb366jw1e7oseux1hbj20n306xq40.jpg)
 
 点击「login」进入下图界面。

 ![](http://ww2.sinaimg.cn/large/5e8cb366jw1e7osfs2qz2j20hm06x0tz.jpg)
 「From Data」里面数据比较多，通常需要用户名、密码，其余的数据是否必要，需要测试一下。对于这个网站，还需要「formhash」。

2. Linux下无编码问题，win下如果出现编码问题应该是终端对编码的支持不到位。

3. 登录成功之后，我们创建的cookie_handler会自动管理cookie，程序的后面如果需要访问其他页面，用opener打开其url即可。

4. 「User-Agent」同样可以通过F12查看到。

5. 更详细更nice的说明请参考[这里](http://blog.csdn.net/wxg694175346/article/category/1418998)

6. 这篇博客重点不在介绍原理，重点是记录下这个简单的代码块，其他需要登录的爬虫仿写就可以了。

这个程序的目的是批量下载mlook的电子书。现在遇到一个问题：

下载时网站会验证cookie，不通过就没法下载。但是，我们用python下载文件一般是通过`urllib.urlretrieve()`。问题来了，这种方式没办法跟opener绑定到一起。

一种可能的解决办法是用opener打开下载链接，用open和write方式保存。但这个方法消耗比较大。

程序完成后会共享到这里。

---

爱打卡-100days-第80天-0111
