title: python学习之re模块
date: 2013-07-29 09:28:02
categories: python
tags: 正则表达式
---
这几天玩爬虫已经使用了很多次的re模块，算是比较熟悉了，这里梳理一下。

首先，关于正则表达式的概念，[这里](http://blog.csdn.net/wxg694175346/article/details/8929576)有最好的教程。

对于正则表达式，我们可以先用compile方法编译为pattern对象，再调用相关的方法进行模式匹配，也可以直接进行匹配。

<!--more-->

对于第一种，示例如下：

```python
import re
pat = re.compile(r'e(.*?)o') #编译为pattern对象
text = 'Hello world' #要匹配的文本
mat = pat.match(text) #从text开头进行匹配，开头不符合就over，返回一个match对象，通过group（）方法获取对应元组
src = pat.search(text) #在整个text中搜索，第一次找到就返回，通过group（）方法获取对应元组
spl = pat.split(text) #用pat进行匹配，并以匹配的文本为界分割text，返回列表
fdl = pat.findall(text) #在text中搜索所有匹配的内容，返回列表
sub = pat.sub(s,text) #用pat进行匹配，然后把匹配内容替换为s，返回替换之后的字符串
sbn = pat.subn(s,text) #同上，但返回字符串和替换次数构成的元组
fdi = pat.finditer(text) #返回迭代器
```

对于第二种，相应代码为：

```python
import re
text = 'Hello world'
mat = re.match(r'e(.*?)o',text)
src = re.search(r'e(.*?)o',text)
spl = re.split(r'e(.*?)o',text) 
fdl = re.findall(r'e(.*?)o',text)
sub = re.sub(r'e(.*?)o',s,text)
sbn = re.subn(r'e(.*?)o',s,text)
fdi = re.finditer(r'e(.*?)o',text)
```

返回结果和第一种一样，使用方法也有明显的规律，就是把正则表达式放在第一个参数位置。

值得注意的是，在第一种的re.compile()和第二种的方法中，都可以附加一个额外的参数用来标明匹配模式，放在最后面。

可选值有：
 
 re.I(全拼：IGNORECASE): 忽略大小写（括号内是完整写法，下同）  
 re.M(全拼：MULTILINE): 多行模式，改变'^'和'$'的行为（参见上图）  
 re.S(全拼：DOTALL): 点任意匹配模式，改变'.'的行为  
 re.L(全拼：LOCALE): 使预定字符类 \w \W \b \B \s \S 取决于当前区域设定  
 re.U(全拼：UNICODE): 使预定字符类 \w \W \b \B \s \S \d \D 取决于unicode定义的字符属性  
 re.X(全拼：VERBOSE): 详细模式。这个模式下正则表达式可以是多行，忽略空白字符，并可以加入注释。  
 
可以使用类似`re.I | re.M`形式，使这两种模式同时生效。

---
爱打卡-100days-第62天-1111