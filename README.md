## Hexo+Github Page搭建个人博客

[我的博客](https://wgjh5.github.io/)

### 安装前提

安装 Hexo 相当简单。然而在安装前，您必须检查电脑中是否已安装下列应用程序：

- [Node.js](http://nodejs.org/) (至少nodejs 6.9)
- [Git](http://git-scm.com/)

#### 1.先全局安装脚手架

````bash
npm install hexo-cli -g
````

#### 2.搭建博客文件夹

````bash
hexo init blog
````

#### 3.进入建好的文件夹并安装依赖

````bash
cd blog
npm install
````

#### 4.开启服务

````js
hexo  server 
//简写
hexo s
````

[官方文档](https://hexo.io/zh-cn/)

### 选择主题

[主题链接](https://hexo.io/themes/)

> 我选择的主题是 `ocean`

### 安装

```bash
$ git clone https://github.com/zhwangart/hexo-theme-ocean.git themes/ocean
```

### 启用

目录 `theme` 中 `_config.yml` 选择 `theme: ocean`

```bash
theme: ocean
```

### 更新

```bash
$ cd themes/ocean
$ git pull
```

### 配置

默认开启**相册**与**关于**菜单，关闭 **Gitalk** 评论功能，需要的同学 `true` 就可以了，[关于 Gitalk 的使用](https://zhwangart.github.io/2018/12/06/Gitalk/) 过程中遇到各种报错，有同样问题的，或者有兴趣想要了解 Gitalk 可以移步看一看。

```bash
# Menu
menu:
  主页: /
  归档: /archives
  相册: /gallery
  关于: /about
rss: /atom.xml

# Miscellaneous
favicon: /favicon.ico
brand: /images/hexo.svg

# Ocean 主页视频
# 多种格式的视频用于支持不同的浏览器，这里只需要配置好路径，前提是我把视频相关文件统一目录存放。
ocean:
  overlay: true      # 可选，false 则 Ocean 视频下方的笔触式遮盖不显示
  path: /images/ocean/      # 视频统一存放路径，格式 mp4/ogg/webm
  brand: /images/hexo-inverted.svg      # 可选，一个小 Logo

# 内容
excerpt_link: 阅读全文...
share_text: 分享
nav_text:
  page_prev: 上一页
  page_next: 下一页
  post_prev: 前一篇
  post_next: 后一篇

# fancybox
fancybox: true

# Local search
search_text: 搜索

# Gitalk
gitalk:
  enable: false      # 默认关闭评论 开启：true
  clientID:      # 申请 GitHub Application 网页上对应的 Client ID 与 Client Secret 参数
  clientSecret:      # 同上
  repo:      # 创建的仓库名称
  owner:      # Github ID
  admin:      # Github ID
```

**Ocean** 使用了 [feathericon](https://feathericon.com/) 图标库，菜单中的图标定义在“CSS source / css / _partial / navbar.styl”中，可根据需要进行更改或添加。
如果你不需要开启 **相册** 与 **关于** 菜单，需要删除或者注销掉他们的图标，如下边的示例：

```
.nav-item
  &:nth-child(1)         // 主页
    .nav-item-link
      &::before
        content '\f12f'
  &:nth-child(2)         // 归档
    .nav-item-link
      &::before
        content '\f12a'
  //&:nth-child(3)         // 相册
  //  .nav-item-link
  //    &::before
  //      content '\f1a9'
  //&:nth-child(4)         // 关于
  //  .nav-item-link
  //    &::before
  //      content '\f174'
```

如果你想要开启 **Tag（标签）**、**Categories（分类）** 在菜单中显示，请看这里：[关于 Ocean 使用中的问题](https://zhwangart.github.io/2019/07/02/Ocean-Issues/)

### 插件

- **本地搜索** - 使用插件 [hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 生成 `xml` 索引文件。

  ```
  $ npm install hexo-generator-searchdb --save
  ```

  然后为 hexo 的配置文件 `_config.yml` 添加插件配置（注意：不是主题的配置文件，主题配置文件 Ocean 已经配置完成）：

  ```
  # hexo-generator-searchdb@1.0.8
  search:
    path: search.xml
    field: post
    format: html
    content: true
  ```

- **RSS** - 如果您想启用RSS，还需要 [hexo-generate-feed](https://github.com/hexojs/hexo-generator-feed) 插件，仅安装即可，Ocean 已经配置完成。

  ```
  $ npm install hexo-generator-feed --save
  ```

### 文章封面图

需要写在 markdown 的 Front-matter 区域：

```
---
title: Post name
photos: [
        ["img_url"],
        ["img_url"]
        ]
---
```

需要**注意**的是，这里说的封面图并不是文章配图，文章配图按照 markdown 的语法写就好了！

### 相册

首先需要创建一个 page ，关于页面也一样需要创建。

```
$ hexo new page gallery
```

然后在编辑 markdown 的时候需要写在 Front-matter 部分，这种写法可能不是特别特别的好，希望能有更好的方法。

```
---
title: Gallery
albums: [
        ["img_url","img_caption"],
        ["img_url","img_caption"]
        ]
---
```

### 文章置顶

安装插件 [hexo-generator-index-pin-top](https://github.com/netcan/hexo-generator-index-pin-top)：

```
$ npm uninstall hexo-generator-index --save
$ npm install hexo-generator-index-pin-top --save
```

在需要置顶的文章的 Front-matter 区域加上 `top: ture` ，示例：

```
---
title: 新增文章置顶
author: zhwangart
date: 2019-07-18 15:45:03
top: ture
---
```

### 部署到 Github

安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)。

修改配置：

```
deploy:
  type: git
  repo: <repository url> #https://bitbucket.org/JohnSmith/johnsmith.bitbucket.io
  branch: [branch] #published
  message: [message]
```

> 参考资料：<https://hexo.io/zh-cn/docs/deployment>

[使用 Ocean 过程中遇到了问题？](https://zhwangart.github.io/2019/07/02/Ocean-Issues/)

[ocean原文链接](https://zhwangart.github.io/2018/11/30/Ocean/)

[Gittalk评论的使用](https://zhwangart.github.io/2018/12/06/Gitalk/)