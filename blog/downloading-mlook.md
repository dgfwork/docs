title: 批量下载mlook电子书 
date: 2013-08-18 17:23:40
categories: python
tags: 爬虫
---
![](http://webbies.dk/assets/templates/SudoSlider/images/download_box.png)

这几天断断续续完成了这个爬虫程序，功能是批量下载<http://mlook.mobi/>中mobi和epub格式的电子书。

中间遇到了几个困难，个个耗费了我不少心神。目前这个程序已经可以正常使用，但还有许多值得改进的地方。我把脚本放在gist，日后更新版本后会直接在本篇博客中显示。

<!--more-->

先贴代码：

<script src="https://gist.github.com/zippera/6260748.js"></script>

几点说明：

1. 使用时在该脚本目录下运行`python mlook_ebooks.py`并输入要下载页数即可自动下载。

2. 该程序依赖第三方包：requests和BeautifulSoup4。

3. 只下载mobi和epub格式，其他格式没意思。

4. 改程序改到比较满意后会详细介绍其中用到的技术。

---
####推荐

Youtube视频下载插件：[点此获得](http://pan.baidu.com/share/link?shareid=488296723&uk=1661888259)

使用方法：下载之后，拖到chrome的「扩展程序」页面即可自动安装。再打开youtube的视频页面就可以在下边看到下载按钮了，可以选择各种画质进行下载。

---
爱打卡-100days-第82天-0111
