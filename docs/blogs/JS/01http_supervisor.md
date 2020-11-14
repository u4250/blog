---
title: http相关模块使用
date: 2020-11-12
tags:
 - 入门
categories:
 - nodejs
---

## nodejs创建http服务

### 使用http模块

```js
var http = require('http');
/*
    resques 获取url参数
    response 返回响应

*/
http.createServer(function (request, response) {
    //设置响应头
  response.writeHead(200, {'Content-Type': 'text/plain'});
  response.end('Hello World');
}).listen(8081);

console.log('Server running at http://127.0.0.1:8081/');
```

### 解析url

```js
url.parse() //解析 URL 第二个参数为ture时返回对象，通过.query获取参数
url.format(urlObject) //是上面 url.parse() 操作的逆向操作
url.resolve(from, to) //添加或者替换地址
```

### Nodejs 自启动工具 supervisor

`supervisor`这个模块可以随之监控用户修改并执行，省去了用户每次修改完程序再输一遍node ***.js的麻烦

```js
npm install -g supervisor  //安装
```



## nodejs模块

- **核心模块**

​		由一系列简洁而高效的JavaScript库组成，它为Nodejs提供了最基本的api，这些核心模块被编译为二进制分发，并在Nodejs进程启动时自动加载。

- **文件模块**

​	文件模块则是在运行时动态加载，需要完整的路径分析、文件定位、编译执行过程、速度相比核心模块稍微慢一些。

​	1.我们可以把公共的功能抽离成为一个单独的js 文件作为一个模块,默认情况下面这个模块里面的方法或者属性，外面是没法访问的。如果要让外部可以访问模块里面的方法或者属性，
就必须在模块里面通过 exports或者 module.exports暴露属性或者方法。
​	2．在需要使用这些模块的文件中，通过reTuire的方式引入这个模块。这个时候就可以使用模块里面暴露的属性和方法。