---
title: 小程序踩坑
date: 2020-12-27
tags:
 - 踩坑
categories:
 - mpvue
---

## 一.云函数在回调中不执行

`在云函数中操作数据库时，明明操作成功了，理应回调success，却没有；而在小程序端，一样的代码，却能成功回调。`

#### **原因:**在 wx-server-sdk 中不再兼容 success、fail、complete 回调，总是只会返回 Promise。

::: right
来自 [官方文档最后](https://developers.weixin.qq.com/miniprogram/dev/wxcloud/reference-server-api/init.html)
:::

解决办法:在云函数中，回调时别使用success, fail, complete。应该用Promise风格的写法来代替，即数据库操作完毕后，用then()。

```js
await db.collection('users').add({
  data: {
    a: "one",
    b: "two",
  },
}).then(res => {
  fun1()
})
```

