---
title: nodejs文件操作
date: 2020-11-14
sidebar: 'auto'
categories:
 - nodejs
---

## fs模块

### 1.检测是文件还是目录

```js
const fs=require('fs');
fs.stat(path,(err,data)=>{
    if(err){
        console.log(err);
        return;
    }
    console.log(data.isFile())
})  
```

### 2.创建目录

```js
fs.mkdir(path,(err)=>{
         if(err){
             console.log(err);
             return;
         }
    console.log("创建成功")
})
```

### 3.创建写入文件

`存在就替换`

```js
fs.writeFile(filename,string,(err)=>{
    
})
```

### 4.追加写入文件

`不存在会创建`

```js
fs.appendFile(filename,string,(err)=>{
    
})
```

### 5.读取文件

```js
fs.readFile(path,(err,data)=>{
    if(err){
        
    }
    console.log(data.toString());
})
```

### 6.读取目录

```js
fs.readdir(path,(err,data)=>{
    if(err){
        
    }
})
```

### 7.重命名

`重命名或移动文件`

```js
//同以目录下的文件更名：
fs.rename('125.txt','126.txt', (err)=>{
 if(err){
  throw err;
 }
 console.log('done!');
})
 
//不同路径下的文件更名 + 移动：（新的路径必须已存在，路径不存在会返回异常）
var fs = require('fs');
fs.rename('125.txt','new/126.txt',(err)=>{
 if(err){
  throw err;
 }
 console.log('done!');
})
```

### 8.删除文件，目录

```js
//删除目录
fs.rmdir(path,(err)=>{
    if(err){
        
    }
    console.log('成功')
})
//删除文件
fs.unlink(path,(err)=>{
    if(err){
        
    }
    console.log('成功')
})
```

