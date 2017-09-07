title: python爬虫：糗百图片
date: 2013-07-26 09:34:32
categories: python
tags: 爬虫
---
学习python少不了写爬虫，不仅能以点带面地学习、练习使用python，爬虫本身也是有用且有趣的，大量重复性的下载、统计工作完全可以写一个爬虫程序完成。

用python写爬虫需要python的基础知识、涉及网络的几个模块、正则表达式、文件操作等知识。昨天在网上学习了一下，写了一个爬虫自动下载「糗事百科」里面的图片。源代码如下：

<!--more-->

```python
# -*- coding: utf-8 -*- 
# 上面那句让代码里支持中文

#---------------------------------------  
#   程序：糗百图片爬虫  
#   版本：0.1  
#   作者：赵伟  
#   日期：2013-07-25  
#   语言：Python 2.7  
#   说明：能设置下载的页数。没有做更多抽象和交互方面的优化。  
#--------------------------------------- 

import urllib2
import urllib
import re

#正则表达式，用来抓取图片的地址
pat = re.compile('<div class="thumb">\\n<img src=\"(ht.*?)\".*?>')

#用来合成网页的URL
nexturl1 = "http://m.qiushibaike.com/imgrank/page/"
nexturl2 = "?s=4582487&slow"

#页数计数
count = 1

#设置抓取的页数
while count < 3:

    print "Page " + str(count) + "\n"
    myurl = nexturl1 + str(count) + nexturl2
    myres = urllib2.urlopen(myurl)#抓取网页
    mypage = myres.read()#读取网页内容
    ucpage = mypage.decode("utf-8") #转码

    mat = pat.findall(ucpage)#用正则表达式抓取图片地址
        
    count += 1;
    
    if len(mat):
        for item in mat:
            print "url: " + item + "\n"
            fnp = re.compile('/(\w+\.\w+)$')#下面三行分离出图片文件的名称
            fnr = fnp.findall(item)
            fname = fnr[0]
            urllib.urlretrieve(item, fname)#下载图片
	    	
    else:
        print "no data"
```

使用方法：新建一个practice文件夹，将源代码保存为`qb.py`文件，并放在practice文件夹中，在命令行里执行`python qb.py`，即开始下载图片。可以修改源代码里面的while语句设置下载的页数。

*资料推荐：<http://blog.csdn.net/wxg694175346/article/category/1418998>*

---
爱打卡-100days-第59天-1111