title: python学习之yield
date: 2013-07-30 09:25:39
categories: python
tags:
---
python中有一个略微奇怪的表达式叫yield expression，本文就来探究一下这是个什么东西。一步一步来。

####iterable

```python
mylist = [1,2,3]
for item in mylist:
    print str(item)
```

mylist是一个列表（list），我们可以逐条取出每一个item，这个过程叫做iteration。像list这样可以用"for...in..."依次遍历的对象被称为iterable，其他的iterable还有string、tuple、dict等。iterable的一个特点是所有的item会存储到内存中，这样会产生一些不便和不利的地方，于是催生了generator（后面讲到）。


<!--more-->

####list comprehension(列表推导式)

```python
mylist = [x*x for x in range(3)]
```

表达式右边是一个for循环的简写形式，用`[]`包裹起来（称为list comprehension），表达式的值是一个list，我们可以像普通list那样使用"for...in..."遍历其元素，如：

```python
for item in mylist:
    print str(item)
```

####generator

对上面的list comprehension稍作修改：

```python
mygenerator = (x*x for x in range(3))
for item in mygenerator:
    print item
```

可以看到只是把`[]`换成了`()`，这时表达式的值不再是list，而是一个generator。

generator也属于iterable，但是其调用方式非常特别。

####yield

```python
def creatGenerator():
    mylist = range(3)
    for x in mylist:
        yield x*x
        
mygenerator = creatGenerator()

for x in mygenerator:
    print(x)
```

yield的使用方法和return是一样的。但是（重点来了）：

* 第6行中调用函数的时候，函数体并不执行，只是简单返回一个generator对象。
* 第8行的for循环，每次遍历mygenerator的一个item：creatGenerator()函数体开始执行，直到函数体执行到`yield x*x`便中断运行，返回一个迭代值。下一次循环，函数体从上一次`yield x*x`的下一条语句开始执行...直到不再执行yield expression为止（generator 自动抛出 StopIteration 异常，表示迭代完成。在 for 循环里，无需处理 StopIteration 异常，循环会正常结束。）

####什么时候用yield？

* mylist只使用一次，或者mylist特别长，由于不用全部保存到memory，所以执行起来又快又省空间。
* 函数体需要返回多值的时候。和yield不用，return语句第一次出现函数便结束，如
  ```python
  def myfunc1():
      yield 1
      yield 2
      yield 3
  
  def myfunc2():
      return 1
      return 2
      return 3
  ```
  
  第一个函数会返回一个generator对象，使用这个对象可以依次获得全部三个输出。第二个函数只有一个输出1，后面的return语句不会执行。
  
  当然，稍作修改的话，也可以使用return返回多值：
  
  ```python
  def myfunc3():
      result = []
      for x in range(3):
          result.append(x)
        
      return result
  print myfunc3()
  ```
  
参考资料：<http://stackoverflow.com/questions/231767/the-python-yield-keyword-explained>  

---
爱打卡-100days-第63天-0111