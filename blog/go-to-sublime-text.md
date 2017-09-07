title: 初识Sublime Text
date: 2013-08-25 19:40:23
categories: IT杂谈
tags:
---
![](http://ww1.sinaimg.cn/large/5e8cb366jw1e7z6jqyv1hj211y0kqwi1.jpg)

看到很多人推荐神器**Sublime Text**，我今天也来玩玩。

官网的一句话广告：

>Sublime Text is a sophisticated text editor for code, markup and prose.

维基百科的一句话简介：

>Sublime Text 是一套基于 Python 的跨平台文字编辑器。最初设计为 Vim 编辑器的多功能扩充软件。

注意Sublime Text和**python、vim**的渊源，后面我们就会看到了。

*声明：以下均为windows下操作，其他系统未测试。*

<!--more-->

###安装

去[官网](http://www.sublimetext.com/)下载和安装相应的版本。对于windows用户，有*安装版*和*绿色版*可选。推荐使用**安装版**。

*注意：最新版本为3测试版，推荐下载2！*

软件安装好了之后不需要任何配置就可以使用了。最常用的设置Sublime Text已经帮我们做好了，打开直接享用！

###插件管理

一个NB的编辑器之所以NB，插件支持是一个重要的元素。Sublime Text有一个插件管理器是必装的。

`ctrl+`打开**Console**，把下面的代码复制进去：

```
import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')
```
回车键。

重启，如果看到`Preferences > Package Control`就说明成功了。

如果上面的方法安装失败，使用下面这个办法：

1. Click `the Preferences > Browse Packages…`menu
2. Browse up a folder and then into the `Installed Packages/` folder
3. Download [Package Control.sublime-package](https://sublime.wbond.net/Package%20Control.sublime-package) and copy it into the `Installed Packages/` directory
4. Restart Sublime Text

插件管理器搞定之后，就可以随意安装插件了。方法很简单：

`ctrl+shift+p`，输入`ip`，看到「Install Package」，回车键。然后出现插件列表，在里面输入要找的插件，比如**tag**，选中并回车即可自动安装好。

###常用插件

我今天才开始用，安装的插件很少。下面是网友推荐的几个，我只安装了一部分。

- tag：Html格式化，右键Auto-Format Tags on Ducument。

- ZenCoding：不得不用的一款前端开发方面的插件，Write less , show more.安装后可直接使用，Tab键触发，Alt+Shift+W是个代码机器。

- SideBarEnhancements：侧栏右键功能增强，非常实用。

- Theme–Soda：完美的编码主题，用过的都说好，Setting user里面添加”theme”: “Soda Dark.sublime-theme”。

- SublimeLinter：这是用来在写代码时做代码检查的。可以在包管理器中安装。写Python程序的话，它还会帮你查代码是否符合PEP8的要求。有问题有代码会出现白框，点击时底下的状态栏会提示出什么问题。

- Python PEP8 Autoformat：这是用来按PEP8自动格式化代码的。可以在包管理器中安装。如果以前写程序不留意的话，用SublimeLinter一查，满屏都是白框框，只要装上这个包，按ctrl+shift+r，代码就会按PEP8要求自动格式化了，一屏的白框几乎都消失了。

- Alignment：代码对齐，如写几个变量，选中这几行，Ctrl+Alt+A，哇，齐了。

###快捷键

前面说过，Sublime Text跟Vim渊源极深，软件安装好之后也是默认支持Vim模式的。所以很多vimer熟悉的快捷键和操作方式在这里同样使用，甚至也分为普通模式和插入模式，但命令模式有很多不同。

这里只列举最有用且不同于vim的一些快捷键，以后发现更多好用的后会再行补充。

- `ctrl+shift+p` 打开命令提示窗口，你所要的，这里都有:)
- ``ctrl+` `` 打开console
- `ctrl+r` 查找函数和块，非常有用
- `ctrl+/` 注释和解注释
- `ctrl+p` 切换打开的文件
- `ctrl+w` 关闭当前标签页
- `ctrl+shift+w` 关闭所有打开的标签页
- `ctrl+m` 跳转到该位置前后的括号
- `ctrl+k+b` 开关侧边栏
- `alt+n` 快速切换到第n个打开的标签页
- `F11` 全屏模式
- `shift+F11` 防打扰模式

###赞许

好看。

方便好用。

###抱怨

markdown的高亮支持惨不忍睹，也没有好用的插件可以替代。

---
爱打卡-100days-第89天-0111

