title: python安装、升级和包管理
date: 2013-08-14 10:19:18
categories: python
tags:
---
![](http://ww4.sinaimg.cn/large/5e8cb366jw1e7m0eyh2i1j20m80go0tk.jpg)

<!--more-->

昨天之前，我win下的python版本一直是2.6.x。最近安装各种第三方包的时候频频出现兼容或依赖方面的错误，版本比较旧，的确改升级了。python的版本分为2系和3系，且各版本之间可以同时存在。由于我前几天看过《Dive into python3》，正好想练习一下，又由于第三方库对python2的支持是最好的，所以我选择同时安装2.7.5和3.3。下面说一下升级的过程（以win7下2.7.5为例）：

1. 安装**python**：到python[官网](http://www.python.org/getit/)下载2.7.5win版的二进制文件，双击安装，设置默认。

2. 修改或添加环境变量：`C:\Python27;C:\Python27\Scripts;`。现在就可以在cmd里面运行`python`了，如果失败，重启cmd再运行。

3. 安装**setuptools**（有了这个才能安装第三方的包）：到[这里](https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py)下载**ez_setup.py**，在其所在的目录下运行`python es_setup.py`即可安装。

4. 安装**pip**（包管理器，可以方便的安装各种第三方包）：到[这里](https://github.com/pypa/pip/releases)下载最新版本的源代码包ø，解压之后进入目录，运行`python setup.py install`即可安装。

5. 安装需要的**第三方包**，以shadowsocks为例，运行`pip install shadowsocks`。如果提示成功，那恭喜你哦了。如果提示`could not fetch url https...`，说明你的ssl和pip不兼容。最好的解决办法是，回到第4步，下载1.2版本并安装。这个版本会默认通过http方式获得包，而不是https。

好人做到底，再列举一下pip最常用的几个命令：

* `pip install foo`	   安装包foo

* `pip uninstall foo`   卸载包foo

* `pip install -upgrade foo`	升级包foo

* `pip show --files foo`	显示包foo所在目录

* `pip list --outdated`    列出需要升级的包

---
爱打卡-100days-第78天-0111
