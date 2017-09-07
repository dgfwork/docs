title: elementary os 
date: 2013-08-22 18:28:36
categories: linux
tags:
---
把Ubuntu系统删除之后，在win7上装了虚拟机运行elementary os，一个设计出色的类ubuntu的linux发行版。简要记录一下过程，**并分享几张截图**。

###安装Vmvare

首先安装虚拟机。我的笔记本是win7 32位系统。

1. 下载[VMware9-workstation_官方原版+完美稳定的汉化补丁+VMware9注册机.rar](http://pan.baidu.com/share/link?shareid=2928125003&uk=1661888259)，并解压。

2. 根据文件夹里的说明进行安装。

安装过程可能遇到一个图示的问题：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1e7vn5a0rgxj209w05cjrj.jpg)

解决办法是：

1. 在运行中键入 “regedit” 获取注册表
2. 删除 HKEY_LOCAL_MACHINE\SOFTWARE\VMware, Inc.
3. 重新安装VMware即可。

<!--more-->

###安装elementary os

1. 下载[elementaryos-stable-i386.20130810.iso](http://pan.baidu.com/share/link?shareid=2964731970&uk=1661888259)。

2. 运行vmware，进行安装。[这里](http://www.cnblogs.com/achillesyang/archive/2012/06/21/2557152.html)有详细的图文说明，虽然是ubuntu，但区别不大。

需要说明的是：

* 在**网络配置**那一步，选择NAT就可以了，安装好之后不用设置即可上网。
* 内存大小选择1G，硬盘大小8G，CPU选择双核。

###晒图

好了，安装过程很简单，这里把elementary os系统截图分享给大家。

![启动画面](http://ww4.sinaimg.cn/large/5e8cb366jw1e7vmppa7u8j20vo0f40sy.jpg)

![漂亮的桌面和终端](http://ww2.sinaimg.cn/large/5e8cb366jw1e7vmr7lie1j211s0lcgt4.jpg)

![自带浏览器](http://ww3.sinaimg.cn/large/5e8cb366jw1e7vmrq1scgj211s0lcacy.jpg)

![文件浏览器](http://ww4.sinaimg.cn/large/5e8cb366jw1e7vmshrv63j211s0lctdh.jpg)

---

###PS

1. 今天百度1元1T永久网盘空间。360随后推出免费1T永久网盘空间。网民乐开花。

2. 济南中院对薄熙来案子公开审理，中院官方微博进行图文直播，「庭审现场」详细叙说庭审的过程，我从早上跟到了傍晚，很有意思。

---
爱打卡-100days-第86天-0111
