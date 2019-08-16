---
title: vue给js加版本号
author: wgj
date: {{ date }}
authorDesc: 一个写代码的「伪文人」
categories: 技术
tags:
    - vue
    - vue给js加版本号
keywords:
comments: true 
---
#### 在`build`文件里面的`webpack.prod.conf.js`文件里面加如下代码
<!-- more -->
````js
    // 版本号
const Version = new Date().getTime();



//把output那段改成如下代码
output:  {         
    path:  config.build.assetsRoot,         
    filename:  utils.assetsPath('js/[name].[chunkhash].'  +  Version  +  '.js'), 
    chunkFilename:  utils.assetsPath('js/[id].[chunkhash].'  +  Version  +  '.js')     
},
    
    
    
  //  把new ExtractTextPlugin 改成如下代码
new ExtractTextPlugin({
    filename: utils.assetsPath('css/[name].[contenthash]' + Version + '.css'),
        allChunks: true
    }),
````

![Version](.\img\Version.png)

![top](.\img\top.png)

![output](.\img\output.png)

![bottom](.\img\bottom.png)