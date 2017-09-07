title: 初识node.js
date: 2013-06-05 14:58:08
categories: hexo
tags: [hexo,node.js]
---
这几天在V2EX看到很多*node.js*相关的招聘贴，有招后端的，有招前端的，多是初创公司，可以看出*node.js*的火热程度。正好我所用的博客框架*hexo*是基于*node.js*的，本就想了解下*hexo*的工作原理，再加上众多招聘贴金光闪闪的刺激，学习*node.js*的兴致就上来了。

原来跟过[《Node入门》](http://www.nodebeginner.org/index-zh-cn.html)这个教程，学习时也做了些笔记。这次找到另外一个教程[《深入浅出Node.js》](http://www.infoq.com/cn/master-nodejs)，更加侧重背景技术的介绍。现在根据我的学习，对*node.js*做个简单介绍。

*node.js*这个词，后缀是*.js*，是不是一种javascript程序呢？非也。javascript是使用最多的前端技术，由浏览器解析后呈现在用户面前。而*node.js*是一项后端技术，准确的说，它既提供了后端的运行时环境，又是一个库。

那与javascript有关系没有？有。首先，*node.js*的语法同javascript。其次，*node.js*用的引擎是Chrome浏览器用于解析javascript的V8引擎。正因为与javascript关系紧密，很多前端可以更为轻松地转为*node.js*后端开发。

*node.js*于2009年诞生，创始人是 Ryan Dahl。它采用C++语言编写而成，是一个Javascript的运行环境。*node.js*采用了Google Chrome浏览器的V8引擎，性能很好，同时还提供了很多系统级的API，如文件操作、网络编程等。

*node.js*的特点是：事件驱动、异步编程，为网络服务而设计。回调函数注册后，等待事件的触发，而无需阻塞等待，这样充分利用了服务器的资源。

*node.js*的安装很简单，在 Windows 环境下安装 Node.js，仅须[下载](http://nodejs.org/)安装文件并执行即可完成安装。

安装完成后，通过`node -v `命令可以查看是否安装成功，成功则显示*node.js*的版本。

使用：创建一个example.js。
```
var http = require('http'); 
http.createServer(function (req, res) { 
    res.writeHead(200, {'Content-Type': 'text/plain'}); 
    res.end('Hello World\n'); 
}).listen(1337, "127.0.0.1"); 
console.log('Server running at http://127.0.0.1:1337/'); 
```

运行`node example.js` 执行文件，然后打开浏览器，访问`http://127.0.0.1:1337/`，*node.js*服务器和example.js就运行起来了。

上述安装好*node.js*后，会把一些核心包安装到本地。我们需要使用别人的模块怎么办？神器：NPM。

NPM的全称是Node Package Manager，如果你熟悉ruby的gem，Python的PyPL、setuptools，PHP的pear，那么你就知道NPM的作用是什么了。没错，它就是Nodejs的包管理器。我们使用上述方法安装*node.js*时，默认附带安装好了NPM，不需要另行安装。

使用NPM安装扩展包的方法很简单，`npm install -g 包名`。  
其中的`-g`参数指明我们使用全局路径。这个命令会把模块安装在 `$PREFIX/lib/node_modules` 下，可通过命令 `npm root -g` 查看全局模块的安装目录。  
例如，我想使用hexo搭建博客，需要安装hexo包，应该使用命令`npm install -g hexo`进行安装，安装目录在`C:\Users\zippera\AppData\Roaming\npm\node_modules`，hexo使用的所有包都可以在该目录下找到。

如何创建自己的模块，并在适当的地方使用呢？通过下面的例子就能看出来。
```
var PI = Math.PI;
exports.area = function (r) {
    return PI * r * r;
};
exports.circumference = function (r) {
    return 2 * PI * r;
};
```

将这个文件存为circle.js，并新建一个app.js文件，并写入以下代码：
```
var circle = require('./circle.js');
console.log( 'The area of a circle of radius 4 is ' + circle.area(4));
```

在require了这个文件之后，定义在exports对象上的方法便可以随意调用。

好了，既然是初识，就讲到这里、点到为止吧。

现在比较知名的*node.js*用户有LinkedIn、淘宝，*node.js*的优势正在得到越来越多的认可，以后有必要的话会做深入学习。

---
爱打卡-100days-第9天-0111