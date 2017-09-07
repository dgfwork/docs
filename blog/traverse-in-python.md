title: python中文件遍历的几种方法
date: 2013-08-12 13:37:42
categories: python
tags:
---
今天写一个在windows下批量修改文件名的python脚本，用到文件的遍历。用python进行文件遍历有多种方法，这里列举并说明一下。

###os.path.walk()

这是一个传统的用法。

walk(root,callable,args)方法有三个参数：要遍历的目录，回调函数，回调函数的参数（元组形式）。

调用的过程是遍历目录下的文件或目录，每遍历一个目录，调用回调函数，并把args作为参数传递给回调函数。

回调函数定义时也有三个参数，比如示例中的func中的三个参数，分别为walk传来的参数、目录的路径、目录下的文件列表（只有文件名，不是完整路径）。请看示例：

```python
import os
s = os.sep	#根据unix或win，s为\或/
root = "d:" + s + "ll" + s	#要遍历的目录

def func(args,dire,fis):	#回调函数的定义
    for f in fis:
        fname = os.path.splitext(f)		#分割文件名为名字和扩展名的二元组
        new = fname[0] + 'b' + fname[1]		#改名字
        os.rename(os.path.join(dire,f),os.path.join(dire,new))	#重命名

os.path.walk(root,func,())	#遍历
```

这种方法在使用时有个问题，不能递归遍历下一层（这点我还不确定，欢迎指正）。

python的高级版本中加入了os.walk()，比这个好用。

<!--more-->

###os.walk()

原型为：os.walk(top, topdown=True, onerror=None, followlinks=False)

我们一般只使用第一个参数。（topdown指明遍历的顺序）

该方法对于每个目录返回一个三元组，(dirpath, dirnames, filenames)。第一个是路径，第二个是路径下面的目录，第三个是路径下面的非目录（对于windows来说也就是文件）。请看示例：

```python
import os
s = os.sep
root = "d:" + s + "ll" + s	

for rt, dirs, files in os.walk(root):
    for f in files:
        fname = os.path.splitext(f)
        new = fname[0] + 'b' + fname[1]
        os.rename(os.path.join(rt,f),os.path.join(rt,new))
```

这种方式可以递归遍历所有的文件。

###listdir

可以使用os模块下的几个方法组合起来进行遍历。请看示例：

```python
import os
s = os.sep
root = "d:" + s + "ll" + s

for i in os.listdir(root):
    if os.path.isfile(os.path.join(root,i)):
        print i	
```

这里需要注意的是，其中的i是目录或文件名，不是完整的路径，在使用时要结合os.path.join()方法还原完整路径。


遍历搞定之后，文件名的修改可以使用正则表达式做一些高级的处理。

另外，还可以使用os.system(cmd)来调用shell里面的相关命令对文件进行处理，很好很强大。

---
爱打卡-100days-第76天-0111
