title: python多线程编程中join函数的使用
date: 2013-07-28 18:47:18
categories: python
tags:
---
今天去辛集买箱包，下午挺晚才回来，又是恶心又是头痛。恶心是因为早上吃坏东西+晕车+回来时看到车祸现场，头痛大概是烈日和空调混合刺激而成。没有时间没有精神没有力气学习了，这篇博客就说说python中一个小小函数。

由于坑爹的学校坑爷的专业，多线程编程老师从来没教过，多线程的概念也是教的稀里糊涂，本人python也是菜鸟级别，所以遇到多线程的编程就傻眼了，别人用的顺手的join函数我却偏偏理解不来。早上在去辛集的路上想这个问题想到恶心，回来后继续写代码测试，终于有些理解了（python官方的英文解释理解不了，网友的解释也不够详细，只能自己钻）。

<!--more-->

测试用的代码如下：

```python
# coding: utf-8

# 测试多线程中join的功能

import threading, time  
def doWaiting():  
    print 'start waiting1: ' + time.strftime('%H:%M:%S') + "\n"  
    time.sleep(3)  
    print 'stop waiting1: ' + time.strftime('%H:%M:%S') + "\n" 
def doWaiting1():  
    print 'start waiting2: ' + time.strftime('%H:%M:%S') + "\n"   
    time.sleep(8)  
    print 'stop waiting2: ', time.strftime('%H:%M:%S') + "\n"  
tsk = []    
thread1 = threading.Thread(target = doWaiting)  
thread1.start()  
tsk.append(thread1)
thread2 = threading.Thread(target = doWaiting1)  
thread2.start()  
tsk.append(thread2)
print 'start join: ' + time.strftime('%H:%M:%S') + "\n"   
for tt in tsk:
    tt.join()
print 'end join: ' + time.strftime('%H:%M:%S') + "\n" 
```

这个小程序使用了两个线程thread1和thread2，线程执行的动作分别是doWaiting()和doWaiting1()，函数体就是打印「开始」+休眠3秒+打印「结束」，分别附加上时间用来查看程序执行的过程。后面用start()方法同步开始执行两个线程。然后开始循环调用两个线程的join()方法，在此之前和之后都会用print函数做好开始结束的标记。我们主要观察`for tt in tsk: tt.join()`。

join()不带参数的情况下，执行如下：

![](http://ww4.sinaimg.cn/large/5e8cb366jw1e72rsxgr8gj20it06i74w.jpg)

可以看到，两个线程并行执行，进程1在3s后结束，进程2在8s后结束，然后回到主进程，执行打印「end join」。

下面把参数设置成超时2s，即`tt.join(2)`，执行如下：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1e72rtihfr6j20it06iwf3.jpg)

两个线程开始并发执行，然后执行线程1的`join(2)`，等线程1执行2s后就不管它了，执行线程2的`join(2)`，等线程2执行2s后也不管它了（在此过程中线程1执行结束，打印线程1的结束信息），开始执行主进程，打印「end join」。4s之后线程2执行结束。

总结一下：

1. join方法的作用是阻塞主进程（挡住，无法执行join以后的语句），专注执行多线程。
2. 多线程多join的情况下，依次执行各线程的join方法，前头一个结束了才能执行后面一个。
3. 无参数，则等待到该线程结束，才开始执行下一个线程的join。
4. 设置参数后，则等待该线程这么长时间就不管它了（而该线程并没有结束）。不管的意思就是可以执行后面的主进程了。

最后附上参数为2时的程序执行流程表，自己画的orz，这样看起来更好理解。

![](http://ww2.sinaimg.cn/large/5e8cb366jw1e72rwxky2oj21kw16owza.jpg)

---
爱打卡-100days-第61天-1111