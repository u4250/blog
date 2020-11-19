---
title: hello,vue
date: 2020-11-17
categories:
 - vue.js
---

### mustache语法



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	</head>
	<body>
		<div id="app">
			{{message+“1111”}}
            
		</div>
		<script type="text/javascript">
			var app=new Vue({
				el:"#app",
				data:{
					message:"hello vue"
				}
			})
		</script>
	</body>
</html>
```

### v-once

该指令表示元素和组件只渲染一次，不会随数据改变而改变。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	</head>
	<body>
		<div id="app">
            <h2 v-once>{{message}}</h2>
            <h2>{{message}}</h2>
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
                        this.message="1111"
					},
				}
			})

		</script>
	</body>
</html>
```

### v-html,v-text，v-pre

用于解析`HTML`代码

text没啥用

`v-pre`:跳过元素编译过程，不解析**mustache**语法

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	</head>
	<body>
		<div id="app">
            <h2 v-html='url'></h2>
            <h2 v-text='message'></h2>
            <h2 v-pre>{{message}}</h2>
		</div>
		<script type="text/javascript">
			var app=new Vue({
				el:"#app",
				data:{
                    message:'arfadf',
                    url:"<a href='https://www.baidu.com/'>百度一下</a>"
				},
			})

		</script>
	</body>
</html>
```

### v-bind动态绑定class

**动态更新**HTML元素上的属性,绑定class有两种方式：对象语法和数组语法

#### 对象语法：

- 可以绑定多个类

  ```html
  <div id="app">
      <div :class="{'active':isActive}">我真的是黑色的！</div>
  </div>
  ```

  ```js
  var app=new Vue({
      el:'.app1',
      data:{
          isActive:true
      }
  });
  ```

- 可以和普通class共存

```html
<div id="app">
    <div class="title" :class="{'active':isActive}">我真的是黑色的！</div>
</div>
```

- 如果过于复杂可以放在methods，computed中

```html
<div :class="get()">我真的是黑色的！</div>
```

```js
					get:function() {
						return {'active':!this.isActive}
						
					}
```

