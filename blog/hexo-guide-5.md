title: hexo系列教程：（五）hexo博客的优化技巧续
date: 2013-06-02 07:17:28
categories: hexo
tags: [hexo,博客,教程]
---
继续介绍hexo博客的优化和使用。

###添加RSS

hexo提供了RSS的生成插件，需要手动安装和设置。步骤如下：

1. 安装RSS插件到本地：`npm install hexo-generator-feed`
2. 开启RSS功能：编辑`hexo/_config.yml`，添加如下代码：
```
plugins:
- hexo-generator-feed
```
3. 在站点添加链接：
在`themes/light/_config.yml`中，编辑 `rss: /atom.xml`  
在`themes/light/layout/_partial/header.ejs`中，`<ul></ul>`之间，添加一样代码`<li> <a href="/atom.xml">RSS</a> </li>`


###添加sitemap

同样的，我们使用hexo提供的插件，方法与添加RSS类似。

1. 安装sitemap到本地：`npm install hexo-generator-sitemap`
2. 开启sitemap功能：编辑`hexo/_config.yml`，添加如下代码：
```
plugins:
- hexo-generator-sitemap
```
3. 访问`zipperary/sitemap.xml`即可看到站点地图。不过，sitemap的初衷是给搜索引擎看的，为了提高搜索引擎对自己站点的收录效果，我们最好手动到google和百度等搜索引擎提交sitemap.xml。

###设置百度统计、Google Analytics
<!--more-->
到[百度统计](http://tongji.baidu.com/web/welcome/login)和[Google Analytics](http://www.google.com/analytics/)（可能需要穿墙）注册账号、添加网站地址即可，很简单，不详述了。需要注意的是，设置好之后数据要过几个小时才能出现，不用着急。

###购买域名、设置DNS

参考之前的这篇博客[购买域名、设置DNS](http://zipperary.com/2013/05/27/domain-name-and-dns/)

###文章中插入图片

使用markdown写文章，插入图片的格式为`![图片名称](链接地址)`，这里要说的是链接地址怎么写。对于hexo，有两种方式：

1. 使用本地路径：在`hexo/source`目录下新建一个`img`文件夹，将图片放入该文件夹下，插入图片时链接即为`/img/图片名称`。
2. 使用*微博图床*，地址<http://weibotuchuang.sinaapp.com/>，将图片拖入区域中，会生成图片的URL，这就是链接地址。

###加入「fork me on github」

[这里](https://github.com/blog/273-github-ribbons)有 github 给出的教程，把代码插入到任意一个全局的模板文件中就行，比如`layout.ejs`的末尾。


###bug:「warning: LF will be replaced by CRLF」

在`hexo deploy`时，有时会出现这个提示信息`warning: LF will be replaced by CRLF`，虽然看起来挺乱糟糟的，但不影响使用，可以忽略不计。若想不提示，可以使用如下方法：

1. 切换到博客的根目录，执行如下命令：`git config --global core.autocrlf  false`
2. 删除掉该目录下的`.git`文件夹（可能是隐藏的），命令：`rm -rf .git`
3. 重新`git init`。

再deploy试试吧，清新脱俗了。

###bug:`hexo deploy`没反应

好多网友遇到过这个问题，目前来看，主要问题出在config.yml的deploy配置上。注意缩进，同时注意冒号后面要有一个空格。

###bug:`hexo update -g`升级错误，hexo命令失效

我升级时遇到了这个问题，原因不详。这种情况下，可执行`npm install -g hexo`重新安装一遍hexo，效果跟升级一样。各版本所做更新修正，请参考[这里](https://github.com/tommy351/hexo/releases)。

###bug:搜索框进行搜索：没有结果

点击搜索后进入的google页面，搜索框里面是不是显示「site:yoursite.com」，这说明有个地方没有设置，请随我来：

打开根目录下的config文件，第15行，`url:`，自觉填上吧。

###bug:代码块中不显示行号

hexo 的作者已经提示过了，使用四个空格的方式标志代码块的确没行号，需要行号的要使用反引号的方式。

###文件结构

最后，贴上文件结构的截图，供大家参考。

![hexo根目录](/img/zipperary.png)

![source目录](/img/source.png)

---
爱打卡-100days-第6天-1111
