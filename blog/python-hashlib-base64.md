title: python学习之hashlib和base64模块
date: 2013-07-29 08:57:50
categories: python
tags: 加密
---
看到好几位博主通过对模块的各个击破学习python，我也效法一下，本篇说一下python中加密涉及到的模块。

###hashlib

hashlib模块支持的加密算法有md5 sha1 sha224 sha256 sha384 sha512(加密原理请参考[此处](http://msdn.microsoft.com/zh-cn/library/92f9ye3s.aspx))，使用起来也很简单。

<!--more-->

以md5加密为例，有两种方法：

一、 追加模式

 代码示例：
 
 ```python
 import hashlib #引入hashlib模块
 
 mm = hashlib.md5() #创建一个md5对象
 mm.update("Hello") #通过update方法加密文本
 mm.update(" world!") #追加，这两句相当于 mm.update("Hello world!")
 print mm.digest() #输出加密后的二进制数据
 print mm.hexdigest() #输出加密后的十六进制数据
 ```
二、 一句话
 
 如果不需要追加，只用加密一段文本，可用这种形式，代码示例：
 
 ```python
 import hashlib
 
 hashlib.new("md5","Hello world!").digest()
 ```

 
此外，md5等算法对象还提供了`digest_size`和`block_size`等属性，指示加密后文本的大小。

对于其他的加密算法，只要在代码中替换「md5」即可，不再举例。

###base64

这个模块提供的加密算法并不安全，但十分简单，有时候会用到。

代码示例：

```python
import base64

a = "Hello world!"
b = base64.encodestring(a) #加密
c = base64.decodestring(b) #解密

print a==c
```

python还有诸多的第三方模块提供更多的加密方式，以后学到的时候再说。

---
爱打卡-100days-第62天-1111