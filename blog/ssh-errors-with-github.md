title: Git push时重复输入用户名密码的问题
date: 2013-05-26 19:48:49
categories: hexo
tags: [github,hexo]
---
在windows上使用git来push到github服务器的时候，每次都需要填写用户名/邮箱、密码，很麻烦。最近用hexo写博客，需要频繁地进行博客配置和预览，而每次预览执行`hexo deploy`都需要输入用户名、密码验证，不胜其烦，今天下决心解决。

尽管github提供了`SSH`方式进行本地和服务端的链接，可是按照网站说明设置好之后，这个问题仍然得不到解决。尝试了好几次，最终用下面这个方法解决了。
<!--more-->
1. 首先添加环境变量。  
![](http://ww2.sinaimg.cn/large/5e8cb366jw1e51yjjv0okj20b00b5gmp.jpg)
2. 在用户文件夹`如C:\Users\zhangsan`下新建一个名为`_netrc`的文件。
3. 编辑该文件：
```
machine github.com
login zhangsan
password 123456
```
保存。