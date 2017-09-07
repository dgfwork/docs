title: 如何绑定二级域名
date: 2013-06-19 09:59:44
categories: hexo
tags: dns
---
我曾在[购买域名、设置DNS](http://zipperary.com/2013/05/27/domain-name-and-dns/)一文中介绍过『如何在Goddady购买域名，在DNSPod设置域名映射』。本文在此基础上介绍一下怎样绑定二级域名（a.aa.com形式）。

我在『百度开放平台』新建了一个web应用，百度提供了`duapp.com`下的二级域名，如<http://1.yiqiansw.duapp.com/>。也可以自由绑定其他域名。这里以此为例进行介绍。


1. 在百度开发者中心，查看CNAME记录。

 ![](/img/sdns1.png)
 按照上图打开『域名绑定』窗口。我们看到，第一步是『将您的自有域名的CNAME记录指向：yiqiansw.duapp.com』，这里`yiqiansw.duapp.com`是百度默认提供的域名。（该窗口不要关闭，稍后会回来）
 
 <!--more--> 
2. 在[DNSPOD](https://www.dnspod.cn)设置二级域名映射。

 在主域名下面，添加一条CNAME记录。如图：
 
 ![](/img/sdns2.png)
 
3. 回到第一步中打开的窗口，在『自由域名』栏填写`yiqiansw.zipperary.com`。勾选『我承诺自有域名已备案，并同意百度域名绑定法务协议』。点击『确认绑定』。

好了，到这里我们已经成功绑定二级域名，查看<http://yiqiansw.zipperary.com>。

吐槽两句：新浪SAE是收费的，『云豆』用完后直接把我的APP全停了。百度的BAE是后起之秀，趁着未收费之际先寄居于此吧，反正不比SAE差！

---
爱打卡-100days-第23天-0111