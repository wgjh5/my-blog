---
title: vue中v-touch事件用法
author: wgj
date: {{ date }}
authorDesc: 一个写代码的「伪文人」
categories: 技术
tags:
    - vue
    - vue中v-touch事件用法
keywords:
comments: true 
---

#### 1.先下载

```bash
cnpm install vue-touch@next --save dev
```
<!-- more -->
#### 2.在main.js引入

```js
import VueTouch from 'vue-touch'
Vue.use(VueTouch, { name: 'v-touch' })
```

#### 3.用法

```js
<v-touch v-on:swipeup="goRegister">
   <img src="../../assets/img/sign/login.png" alt="">
</v-touch>
```

