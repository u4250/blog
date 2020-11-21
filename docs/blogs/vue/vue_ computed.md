---
title: vue的计算属性
date: 2020-11-20
categories:
 - vue.js
---

## 计算属性

### 计算属性的使用

模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。

```html
<div id="example">
  {{ message.split('').reverse().join('') }}
</div>
```

模板语法内逻辑多导致语句过长影响阅读，这种情况下可以将逻辑写为函数，调用即可，但更为方便的是使用**计算属性**

```html
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>
```

```js
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
      //完整的计算属性包括getter和setter方法
    reversedMessage {
       get: function () {
    },
       set:function(){
      return this.message.split('').reverse().join('')
    }
  }
})
//一般只需要用到getter方法，因此默认的计算属性只包括了getter方法，且简写


var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

### 计算属性与methods方法的不同

两种方式的最终结果确实是完全相同的。然而，不同的是**计算属性是基于它们的响应式依赖进行缓存的**。只在相关响应式依赖发生改变时它们才会重新求值。这就意味着只要 `message` 还没有发生改变，多次访问 `reversedMessage` 计算属性会立即返回之前的计算结果，而不必再次执行函数。