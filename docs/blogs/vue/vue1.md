---
title: vue初体验
date: 2020-11-18
categories:
 - vue.js
---

vue中使用列表与绑定按钮事件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	</head>
	<body>
		<div id="app">
			<ul>
				<li v-for='item in movies'>{{item}}</li>
			</ul>
			<h2>当前计数{{count}}</h2>
			<button v-on:click="add">+</button>
			<button v-on:click="count--">-</button>
		</div>
		<script type="text/javascript">
			var app=new Vue({
				el:"#app",
				data:{
					message:"hello vue",
					movies:['海贼王','大话西游','肖申克的救赎','盗梦空间'],
					count:0
				},
				methods:{
					add:function(){
						this.count++
					},
				}
			})

		</script>
	</body>
</html>
```



### 一.vue中的MVVM模式

### 二.创建vue实例传入的options

- [x] el:
  - 类型：`string`|`HTMLELement`
  - 作用：决定vue实例管理哪个DOM
- [x] data:
  - 类型：`Object `|`Function` (组件当中必须是函数)
  - 作用：vue实例对应的数据对象
- [x] methods:
  - 类型：`{[key:string];Function}`
  - 作用：定义vue方法
- [ ] others：

### 三.vue的生命周期

待补充。。。。