---
title: vue cli3=>vue cli2桥接
author: wgj
date: {{ date }}
authorDesc: 一个写代码的「伪文人」
categories: 技术
tags:
    - vue
    - vue cli3=>vue cli2桥接
keywords:
comments: true 
---

> vue cli3=>vue cli2桥接

#### 1.先安装

```
npm install -g @vue/cli
```
<!-- more -->

#### 2.再安装

```
npm install -g @vue/cli-service-global
```

#### 3.最后安装桥接

```
npm install -g @vue/cli-init

//2.x
vue init webpack my-project
//3.x
vue create my-project
```

 