title: hexo系列教程：（三）hexo博客的配置、使用
date: 2013-05-29 17:28:53
categories: hexo
tags: [hexo,博客,教程]
---
在[上一节](http://zipperary.com/2013/05/28/hexo-guide-2/)中，我们在本地和github搭建起了自己的hexo博客站点，但是还未发表过文章，站点的配置还是原来的默认值。在本节，我们来进行个性化的设置，将站点打造成自己的，同时介绍下怎么撰文和发表。

站点配置用到两个文件，一个是对整站的配置`H:\hexo\_config.yml`，另一个是对主题的配置`H:\hexo\themes\light_config.yml`，我们来分别介绍。

*H:\hexo\ _config.yml*
<!--more-->
```
# Hexo Configuration
## Docs: http://zespia.tw/hexo/docs/configure.html
## Source: https://github.com/tommy351/hexo/

# Site 这里的配置，哪项配置反映在哪里，可以参考我的博客
title: Zippera's blog #站点名，站点左上角
subtitle: Walk steps step by step #副标题，站点左上角
description: Walk steps step by step #给搜索引擎看的，对站点的描述，可以自定义
author: zippera #在站点左下角可以看到
email: #你的联系邮箱
language: zh-CN #中国人嘛，用中文

# URL #这项暂不配置，绑定域名后，欲创建sitemap.xml需要配置该项
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://zipperary.com
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories

# Writing 文章布局、写作格式的定义，不修改
new_post_name: :title.md # File name of new posts
default_layout: post
auto_spacing: false # Add spaces between asian characters and western characters
titlecase: false # Transform title into titlecase
max_open_file: 100
filename_case: 0
highlight:
  enable: true
  backtick_code_block: true
  line_number: true
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Archives 默认值为2，这里都修改为1，相应页面就只会列出标题，而非全文
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 1
category: 1
tag: 1

# Server 不修改
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
logger: false
logger_format:

# Date / Time format 日期格式，不修改
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss

# Pagination 每页显示文章数，可以自定义，我将10改成了5
## Set per_page to 0 to disable pagination
per_page: 5
pagination_dir: page

# Disqus Disqus插件，我们会替换成“多说”，不修改
disqus_shortname:

# Extensions 这里配置站点所用主题和插件，暂默认，后面会介绍怎么修改
## Plugins: https://github.com/tommy351/hexo/wiki/Plugins
## Themes: https://github.com/tommy351/hexo/wiki/Themes
theme: light
exclude_generator:
plugins:
- hexo-generator-feed
- hexo-generator-sitemap

# Deployment 站点部署到github要配置，上一节中已经讲过
## Docs: http://zespia.tw/hexo/docs/deploy.html
deploy:
  type: github
  repository: https://github.com/zippera/zippera.github.io.git
  branch: master
```

现在可以`hexo generate`，`hexo server`，打开`localhost:4000`查看效果了。


*H:\hexo\themes\light_config.yml*
```
menu: #站点右上角导航栏，暂时默认，后面介绍修改
  首页: /
  存档: /archives
  关于: /about
  ToDo: /todolist
  

widgets: #站点右边栏，暂时默认，后面介绍修改和添加
- search
- category
- tagcloud
- weibo
- blogroll


excerpt_link: 阅读全文 #替换为中文

plugins: 


twitter: #右边栏要显示twitter展示的话，需要在此设置
  username: moxie198
  show_replies: false
  tweet_count: 5

addthis: #SNS分享，身在天朝，当然用“百度分享”，暂时默认，后面会介绍
  enable: true
  pubid:
  facebook: true
  twitter: true
  google: true
  pinterest: true

fancybox: true #图片效果，默认

google_analytics: #要使用google_analytics进行统计的话，这里需要配置ID，暂时默认，后面介绍
rss:  #生成RSS，需要配置路径，暂时默认，后面介绍
```

上面改动的不多，更多的是介绍了下功能，后面会相继介绍具体的修改方法。

好了，站点配置好了，我想发表一篇文章，怎么做呢？

1. `hexo new "my new post"`
2. 在`H:\hexo\source\_posts`中打开这个文件（打开方式用“记事本”即可），配置开头。
```
title: my new post #可以改成中文的，如“新文章”
date: 2013-05-29 07:56:29 #发表日期，一般不改动
categories: blog #文章文类
tags: [博客，文章] #文章标签，多于一项时用这种格式
---
#这里是正文，用markdown写，使用方法参照我原来的博客[Introduction to markdown](http://zipperary.com/2013/05/22/introduction-to-markdown/)
```
3. `hexo server`，访问`localhost:4000`预览效果。（退出server用Ctrl+c）
4. `hexo deploy`，同步到github。访问网站看看效果。

现在为止，我们已经搭建起博客，进行一些基本配置，并学会了怎么发表文章。后面会陆续介绍一些高级点的个性化设置，不过在此之前，你可以正常发表博客了。后面的文章你可以不看，有意者请跟随。

---
爱打卡-100days-第2天-1111