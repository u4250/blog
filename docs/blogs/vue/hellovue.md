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

#### 数组语法

。。。。。

### v-on事件绑定

给元素进行**事件**绑定，需要通过v-on:指令实现.

:::tip

鼠标事件：onclick ondblclick onmouseenter onmouseleave onmouseover onmousedown等等

键盘事件：onkeyup onkeydown onkeypress 等等

:::

#### 用法

```html
<p v-on:click="事件处理函数名" ></p>
 
<!-- 简写形式(v-on: 指令可以简写成 @) -->
 
<p @click="事件处理函数名" ></p>   
```

#### 事件处理函数传参

当通过methods定义方法供@click调用时，**需要注意参数问题**。

- 当方法不需要额外的参数时，那么方法后的()可以不加。

  ::: danger
  但如果该方法有一个参数，此时会将原生事件event传入！！！
  :::

- 需要传入参数且同时需要传入event时，可以通过`$event`传入事件

#### 修饰符

### v-if,v-else,v-else-if的使用

```html
			<h2 v-if="message=='hellovue'">ddd</h2>
			<h2 v-else-if="11">11</h2>
			<h2 v-else>??</h2>
```

`当逻辑复杂时不建议使用v-else-if`

小案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	</head>
	<body>
		<div id="app">
			<span v-if="isUser">
				<label for="username">手机号</label>
				<input type="text" id="username">
                <!-- <input type="text" id="username" key="1"> -->
			</span>
			<span v-else>
				<label for="email">邮箱</label>
				<input type="text" id="email">
			</span>
			<button @click="isUser=!isUser">切换</button>
		</div>
		<script type="text/javascript">
			var app=new Vue({
				el:"#app",
				data:{
					isUser:true
				}
			})

		</script>
	</body>
</html>
```

> 此时在点击切换时，输入框里的东西会保留，vue在进行DOM渲染时，出于性能考虑会复用已经存在的元素，解决方法：加input标签里添加 **key**，且不相同。

### v-show

与v-if类似，控制是否显示。

:::tip

当条件为false时

v-if:   该元素不会存在DOM中



v-show：会给元素添加一个行内样式**display：none**

**如何选择？** 根据切换是否显示的次数来选择，如果需要多次切换时选择 **v-show**

:::

### v-for遍历数组



