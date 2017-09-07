title: 恼人的Linux 
date: 2013-08-13 19:33:55
categories: linux
tags: linux
---
![](http://ww1.sinaimg.cn/large/5e8cb366jw1e7lacvg6zcj21hc0xcqc6.jpg)

<!--more-->

看到v2上大家在讨论刚刚发布的elementaryos稳定版，贴图看起来特美，我把系统从百度网盘下载下来，烧录到U盘，修改BIOS的启动项，插入U盘，关机重启（好多天没关过机了），双手合十眼睛汪汪地期待奇迹。然后，尼玛，真奇迹，卡在读取的阶段不动了！懒得折腾了。好容易重启一次，进Ubuntu练习一下这几天学的命令吧。

Ubuntu还是那么惊艳，那么耀眼（显卡驱动坏了无法调低亮度）。开始练习。敲到`cd`命令的时候，心想目录名那么长还有好多特殊字符，真麻烦。然后google，挂了。翻墙吧，Goagent配置失效了。用vpn吧，一会好一会坏的，还不能全局翻（apt-get安装软件的时候慢啊）。用shadowsocks吧，没有二进制的。用nodejs版吧，先装nodejs，各种error：又是缺少依赖包又是文件权限不足，装好依赖包后make吧，这个慢啊，到最后阶段又error了，吐血。算了，python版吧，先装pip，又是缺少依赖包，折腾了一下装好了。装shadowsocks，又是缺少依赖包，折腾一下好了。配置好config之后执行`python proxy.py`，又TM错误，缺少M2crypto包，安装吧，缺少openssl和swig，狂吐。NND，不弄了，继续VPN吧。

软件安装的时候，如果apt-get可以安装那最好，否则，呵呵，config,make,make install...

要在某个目录使用shell，基本上必须用cd从头切换进去，不能直接在目录里调出shell（这点不确定）。

人家说，当初Linus这伙人做Linux的时候就没想着用桌面，这群高人喜欢用命令做一切。不过，话说回来，各种命令配合通配符真的很强大。只能说学习曲线陡峭，投资回报巨大。

早些时候看过《鸟哥的linux私房菜》，内容太多了，怪吓人的，虽然忍着痛苦学习并做了笔记，但之后没怎么用。这次从别的地方学习了一些用的最多的命令，win下用cygwin练习，不会的搜索，一点点积累，再看鸟哥私房菜时感觉就很不同了。

好吧现在又回到了win，不知道下次和ubuntu见面将是何年何月。。。

---

爱打卡-100days-第77天-0111
