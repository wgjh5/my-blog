---
title: vue md5加密用法
author: wgj
date: {{ date }}
authorDesc: 一个写代码的「伪文人」
categories: 技术
tags:
    - md5加密用法
    - vue
keywords:
comments: true 
---



#### 1.先下载md5

```bash
cnpm install js-md5 --save-dev
```
<!-- more -->
#### 2.按需引入

```js
import md5 from "js-md5";

//用法
Pwd: md5(this.password)
```

#### 3.或者在main.js文件中将md5转换成vue原型：

```js
import md5 from 'js-md5';
Vue.prototype.$md5 = md5;
//用法
this.$md5('hello world')  // 5eb63bbbe01eeed093cb22bb8f5acdc3
```
