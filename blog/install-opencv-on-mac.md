title: 在 Mac 上安装 Opencv
date: 2014-03-06 20:23:12
categories: IT杂谈
tags:
---
在 Mac 安装 opencv，使用的方案和 linux 是一样的。

先在[官网](http://opencv.org/)页面右侧下载`OpenCV for Linux/Mac`。

打开终端，用`tar -xvf opencv压缩文件`解压文件。

cd 进入解压后的文件夹。

`mkdir release`

`cd release`

`cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..`

`make`

`sudo make install`

依次执行，最后没报错就是成功了。

我在安装的过程中遇到了一个棘手的问题，大概如下：

```
Linking CXX shared library ../../lib/libopencv_highgui.dylib
[ 35%] Building CXX object modules/video/CMakeFiles/opencv_video.dir/src/bgfg_gaussmix.cpp.o
Undefined symbols for architecture x86_64:
  "_ModPlug_GetCurrentOrder", referenced from:
     _modplug_read_packet in libavformat.a(libmodplug.o)
  "_ModPlug_GetCurrentPattern", referenced from:
     _modplug_read_packet in libavformat.a(libmodplug.o)
  "_ModPlug_GetCurrentRow", referenced from:
     _modplug_read_packet in libavformat.a(libmodplug.o)
  "_ModPlug_GetCurrentSpeed", referenced from:
     _modplug_read_packet in libavformat.a(libmodplug.o)
  "_ModPlug_GetCurrentTempo", referenced from:
     _modplug_read_packet in libavformat.a(libmodplug.o)
  "_ModPlug_GetLength", referenced from:
     _modplug_read_header in libavformat.a(libmodplug.o)
  "_ModPlug_GetMessage", referenced from:
     _modplug_read_header in libavformat.a(libmodplug.o)
  "_ModPlug_GetName", referenced from:
     _modplug_read_header in libavformat.a(libmodplug.o)
```
各种方法都试了，in vain.最后哥们儿帮我找到了答案：

在 cmake 那步，改成：

`cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local .. -DWITH_FFMPEG=OFF`

也就是最后添加了一个参数。什么意思呢？不知道。

参考：

1. [Installation in Linux — OpenCV 2.4.8.0 documentation](http://docs.opencv.org/doc/tutorials/introduction/linux_install/linux_install.html#linux-installation)
2. [c++ - openCV make error - Stack Overflow](http://stackoverflow.com/questions/14517406/opencv-make-error)