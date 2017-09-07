title: jQuery之$.post()
date: 2013-08-03 17:24:39
categories: 前端
tags: jQuery
---
在提交表单时我们可以使用.submit()方法自定义提交表单的动作。提交的方式可以选择get、post、getJSON、getJSONP等等。这里说一下post方式。

`jQuery.post( url [, data ] [, success(data, textStatus, jqXHR) ] [, dataType ] )`

url：要提交的地址，相当于html中的action值。

data：要发送给服务器的数据。

success：这是一个回调函数，如果post成功，会执行该函数。

dataType：这个参数可以设置从服务器返回的数据的格式，可以为xml, json, script, text, html。

<!--more-->

使用示例：

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>jQuery.post demo</title>
  <script src="http://code.jquery.com/jquery-1.9.1.js"></script>
</head>
<body>
  <form action="/" id="searchForm">
   <input type="text" name="s" placeholder="Search..." />
   <input type="submit" value="Search" />
  </form>
  <!-- the result of the search will be rendered inside this div -->
  <div id="result"></div>
 
<script>
/* 使用submit()自定义提交动作 */
$("#searchForm").submit(function(event) {
 
  /* 阻止form正常的提交，使用自定义方式 */
  event.preventDefault();
 
  /* 提取html中的某些元素，这里是要post的数据和地址 */
  var $form = $( this ),
      term = $form.find( 'input[name="s"]' ).val(),
      url = $form.attr( 'action' );
 
  /* 发送数据，使用了url和data这两个参数，后者用字典形式 */
  var posting = $.post( url, { s: term } );
 
  /* 提交成功后的操作，将返回的数据显示在一个div中 */
  posting.done(function( data ) {
    var content = $( data ).find( '#content' );
    $( "#result" ).empty().append( content );
  });
});
</script>
 
</body>
</html>
```

在使用chrome浏览器进行调试时发现一个问题，如果url为http或https，而本文件是在本地打开，post就会失败。这是因为chrome出于安全考虑不支持跨域（file和http）访问。解决的办法，一是用`python -m SimpleHTTPServer 8000`开一个临时的http服务器，一是使用get而非post。

---

爱打卡-100days-第67天-0111