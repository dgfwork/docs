title: linux下常用命令
date: 2013-09-04 09:04:36
categories: linux
tags:
---
![](http://ww3.sinaimg.cn/large/5e8cb366jw1e8bd5xw20jj20mm0gwgmy.jpg)

linux的强大之处，很大程度上在于其丰富灵活的shell命令，但这一点恰恰也是阻碍初学者的老大难问题。这里是我学习linux命令时的笔记，不求全面，但求有用。先学会最基本最常用的命令，在使用中再逐渐积累。

###shell命令行格式

`命令 -l(选项) 参数`   

没有参数的选项可以合并；命令之间用`;`隔开，依次执行；长选项用`--`;管道`|`可以串联执行。

<!--more-->

###系统

md5sum+文件：    检验签名

uname：    机器名    -a详细

history：    命令历史 ；   +10执行第十个

sudo+命令： 超级权限

su moxie： 进入超级用户moxie

passwd：    改密码

alias l='ls -l'：    命令别名  ；  unalias l可以取消

man bla：    帮助

bla --help

whereis ls：   ls 二进制文件的路径

ps：    列出进程

top：    显示cpu信息

free ：   跟踪内存的使用信息    b以B显示    k以KB显示    h易读的格式

kill 5721 ：   杀掉该进程

service bla start：    启动服务    restart、stop

apt-get install bla：    包管理类似pip    update升级

mkpasswd  20：    生成随机密码，长度为20 ???

cal：    日历    02 2000

date：    日期    --set设置

###文件

ls：    列出文件夹、文件    -l  -a

lsof：    显示打开的文件

lsblk：    列出块设备  -l列表形式

df：    磁盘使用情况

mount 分配名 目录 ：   将设备挂在到指定目录

pwd：    print working directory

cd /foo：    改变当前路径    ~    .. . -

mkdir bla：    文件夹

touch bla：    更新时间戳，如果没有，创建

cat a b >>c：    连接ab成c，如果没有c会创建。如果只有a，则显示。    -n行号    cat >>c然后可以输入内容

paste a b >>c：    另一种方式连接

cp bla /foo：    复制

mv...............：    移动，也可以单文件重命名

rm bla foo：    删除    -rf删除目录

rename a b *sh：    多文件重命名，所有sh后缀的文件中的a换成b

cmp foo bar：    比较两个文件

chmod 777 bla：    改权限

chown a:b bla：    改用户和组



find -iname *.sh：    搜索目录和子目录下的文件，i为忽略大小写

grep bla /foobar：    搜索文件中包含bla的行    i忽略大小写    r递归搜索    c统计    color着色

###网络

wget url：    下载

ifconfig：    检查活动路由器    a所有    eth0 down停用    up启用  

netstat：    各种网络相关信息    a所有    t为tcp    s为连接的    c动态输出

dig 某域名：    查询。。。

uptime：    服务器无人值守时发生了什么

w：    uptime和who的组合命令

wall "bla"：    发送一条消息到登录端    类似的还有mesg write talk

###源代码安装

1. tar文件解压

2. `./configure --prefix=/usr`    设置安装到bla，生成makefile

3. `make`    编译

4. `make install`    安装

---
爱打卡-100days-第99天-0001


