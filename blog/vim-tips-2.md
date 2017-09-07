title: Vim Tips 2
date: 2014-05-15 22:48:11
categories: IT杂谈
tags:
---
此前写过一篇[VIM常用命令](http://zipperary.com/2013/09/03/vim-commands/)。Vim 学习曲线还是比较陡峭的，很多教程都是直接给出一个Vim 命令或快捷键的参考列表，求全，这反而把有心学习的潜在用户吓跑了。我在学习使用 Vim 的时候尽量先总结最常用的，并按照操作类型归类，符合自己的认知结构。由此总结出该文中所记述的笔记。写作该文时比较急促，直接把 Evernote 中的 notes 拿过来，没有调整格式，也没有写注解。

有了基础，并能基本使用 vim 编程，以后就是问题驱动型的学习了，aka，coding 中遇到什么不方便的地方，就 google 一下有没有对应的命令、快捷键、插件之类。不久后写了一篇[vim使用中的几个问题](http://zipperary.com/2013/08/24/vim-tips/)。

时间已经过去很久。去年入手 Mac 后，编程几乎都是在 Vim 中，之前用 terminal 的，现在已经习惯使用 Macvim 了。同样基于问题驱动，又 get 了一些技能，在此呈上。

1. 插件管理用`pathogen`，安装插件非常简单，也比`vundle`灵活。
2. `Normal`模式下，寻找上次光标所在位置为`ctrl + o`，下次的为`ctrl + i`，跳到某行修改并返回的时候非常方便。
3. 用`:!command`可以在 Vim 中写 shell 命令，自动转入 shell 执行。不过，我现在一般用`iTerm` + `Macvim`，不再需要用这个命令了。
4. 查看缓存文件`:ls`，是不是很像 shell 中的那个。切换到其中一个用`:buffer n`。
5. File browser 自然使用大名鼎鼎的**NERDTREE**，在 nerdtree 中新建文件的方式是`m-a`并写出文件名称。刷新用`r`。忘记快捷键了，要习惯使用`?`打开和关闭帮助。`Bookmarks`功能刚开始用，赞！
6. 分屏之后切换窗口，用`ctrl + w + h`是切换到左边的窗口，自然，其他方向的分别是`j, k, l`。另外还有两个非常重要，吐血推荐，`t, b`，分别是直接切换到最左或最右，如果你用过`Taglist`并打开了多个窗口，你就知道这东西多重要了。
7. 交换两个窗口的位置，或者说移动窗口，用`ctrl + w + r/x`，试试就知道了，很多时候需要这东西。
8. 窗口大小调整，宽度和高度分别用`ctrl + w + </>`和`ctrl + w + +/-`，或者使用更加灵活的`:res +n`，`:vertical res +n`。自动分割的窗口未必好用，所以很多时候是需要自己调整的。
9. 把鸡肋的 Caps Lock 键换成了 Esc，太爽了。
10. 粘贴到 vim 中时由于 indent 的原因，经常会导致格式乱掉。在`.vimrc`中添加`set pastetoggle=<F9>`，插入模式下按下 F9即可进入粘贴模式，之后再次通过 F9返回即可。

<!--more-->

另外，安装了以下插件：

- [pathogen](https://github.com/tpope/vim-pathogen):方便的插件管理器。
- [nerdtree](https://github.com/scrooloose/nerdtree): 目录树。
- [taglist](http://www.vim.org/scripts/script.php?script_id=273):方便预览代码的block.
- [vim-javascript](https://github.com/pangloss/vim-javascript):改善 vim 对 js 的高亮和语法支持。
- [vim-markdown](https://github.com/plasticboy/vim-markdown)
- [python-syntax](https://github.com/hdima/python-syntax)：直接拷贝的，并修改、添加了对 self 的支持。
- [indentLine](https://github.com/Yggdroot/indentLine)
- [syntastic](https://github.com/scrooloose/syntastic)：语法检查。
- [pep8](https://github.com/jcrocholl/pep8):检查python代码是否符合 pep8规范。
- [Vundle](https://github.com/gmarik/Vundle.vim#about)：插件管理。
- [supertab](https://github.com/ervandew/supertab)
- [jedi-vim](https://github.com/davidhalter/jedi-vim)
- [vim-jade](https://github.com/digitaltoad/vim-jade)
- [html.vim](http://www.vim.org/scripts/script.php?script_id=2075): indent improved
- [emmet-vim](https://github.com/mattn/emmet-vim): zen coding in vim, a tutorial is [here](http://www.zfanw.com/blog/zencoding-vim-tutorial-chinese.html)
- [vim-airline](https://github.com/bling/vim-airline): awsome statusline

vimrc 和插件列表同步在 github 上，从[这里](https://github.com/zippera/vimsettings)进入。

最后上一张效果图：

![](http://ww1.sinaimg.cn/large/5e8cb366jw1egfuz1hon0j21hc0u0tkd.jpg)