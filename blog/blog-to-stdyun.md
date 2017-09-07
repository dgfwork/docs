title: 托管博客到STDYUN
date: 2013-11-13 20:22:52
categories: hexo
tags:
---
![](http://ww3.sinaimg.cn/large/5e8cb366jw1eajpvdib6hj20t70bcdha.jpg)

晚上在[@Ronaldo](http://yuche.me/)的指导下，把博客从*github*迁移到了*stdyun*。前者不必解释，大家都知道。stdyun 是一家国内的云主机服务提供商，对静态网站提供免费的托管服务（限容量，但可申请扩容）。转而使用 stdyun 主要是考虑到这几点：

* 国内主机，速度比 github 快多了。
* 配置很简单，注册到搞定比 github 简单。
* 多人推荐，比较靠谱。
* 虽然只有300M 流量，但对于个人的静态博客够用了，实在不够用的话可以申请免费扩容。

**注意：只能用在mac或linux下！**

<!--more-->

配置也非常简单：

1. 去<https://stdyun.com/>注册帐号，记住用户名和密码；在<https://stdyun.com/octopress>「我的octopress」查看自己的账户和密码。
2. 去博客的`hexo/_config.yml`修改 deploy 配置项，如下：  
 ```
 deploy:
  type: rsync
  host: o.stdyun.net
  user: yourname
  root: ~/www.yourdomain.com/
  port: 22
  delete: true
 ```
3. 现在可以把博客 deploy 到 stdyun 了，使用的命令跟在 github 时是一样的。
4. 修改dns映射。如果要使用二级域名(比如www.domain.com或者blog.domain.com)，添加cname指向cname.stdyun.net
如果要使用顶级域名(比如domain.com)，请添加a记录到218.245.3.110。注意要把原有的映射删掉。

经过这四个步骤，就可以把博客托管到 stdyun 了，非常的方便。
