title: python中的异常处理
date: 2013-08-10 21:02:17
categories: python
tags: 异常处理
---
从几年前开始学习编程直到现在，一直对程序中的异常处理怀有恐惧和排斥心理。之所以这样，是因为不了解。这次攻python，首先把自己最畏惧和最不熟悉的几块内容列出来，里面就有「异常处理」这一项。

《Dive into Python》并没有专门介绍异常处理，只是例子中用到的时候略微说明了一下。今天下载《Learn Python》，直接进异常处理这块。这一部分有四章，第一章讲解异常处理的一般使用方法，后面的章节深入地讨论其机制。我目前只看了第一章，先学会用，以后有必要的时候再扩展阅读。

python主要支持五种异常机制，一一列举。

<!--more-->

###默认的异常处理器

```python
s = 'Hello girl!'
print s[100]
print 'continue'
```
如果我们没有对异常进行任何预防，那么在程序执行的过程中发生异常，就会中断程序，调用python默认的异常处理器，并在终端输出异常信息。这种情况下，第3行代码不会执行。

###try...except

```python
s = 'Hello girl!'
try:
	print s[100]
except IndexError:
	print 'error...'
print 'continue'
```
程序执行到第2句时发现try语句，进入try语句块执行，发生异常，回到try语句层，寻找后面是否有except语句。找到except语句后，会调用这个自定义的异常处理器。except将异常处理完毕后，程序继续往下执行。这种情况下，最后两个print语句都会执行。

except后面也可以为空，表示捕获任何类型的异常。
###try...finally

```python
s = 'Hello girl!'
try:
	print s[100]
finally:
	print 'error...'
print 'continue'
```
finally语句表示，无论异常发生与否，finally中的语句都要执行。但是，由于没有except处理器，finally执行完毕后程序便中断。这种情况下，倒第2个print会执行，到第1个不会执行。如果try语句中没有异常，三个print都会执行。

###assert

```python
assert False,'error...'
print 'continue'
```

这个语句，先判断assert后面紧跟的语句是True还是False，如果是True则继续执行print，如果是False则中断程序，调用默认的异常处理器，同时输出assert语句逗号后面的提示信息。本例情况下，程序中断，提示error，后面的print不执行。

###with...as

```python
with open('nothing.txt','r') as f:
	f.read()
	print 2/0
print 'continue'
```

我们平时在使用类似文件的流对象时，使用完毕后要调用close方法关闭，很麻烦。这里with...as语句提供了一个非常方便的替代方法：open打开文件后将返回的文件流对象赋值给f，然后在with语句块中使用。with语句块完毕之后，会隐藏地自动关闭文件。

如果with语句或语句块中发生异常，会调用默认的异常处理器处理，但文件还是会正常关闭。

这种情况下，会抛出异常，最后的print不执行。

书中介绍的很详细，除了上面我提到的之外，还有很多有用的附加信息，比如`try..except..finally..else`可以连用，比如自定义异常类。这里不再列出，详情可以参考这本书中的介绍。

PS：这本书的翻译真不咋地，跟《Dive into Python》比差很多。

---
爱打卡-100days-第74天-0111
