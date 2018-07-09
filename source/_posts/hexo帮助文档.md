
---
title: hexo帮助文档
date: 2018-07-09 15:35:12
tags:
categories:
  - Blog
  - Hexo
---
# 说明

本文主要是记录一下Hexo的一些功能

<!-- more -->
# 文章中使用图片
https://www.jianshu.com/p/c2ba9533088a
流程：
 1. 修改全局_config.yml中的**post_asset_folder**为**true**
 2. 安装依赖
 ```
 npm install https://github.com/CodeFalling/hexo-asset-image --save
 ```
 3. 调用**hexo n "test-image"**，就会在_post目录下生成同名文件夹，图片放进去后，使用\!\[sola\]\(test-image/sola.jpg)就可以引用图片。
![sola](hexo帮助文档/sola.jpg)

# Live2D
github仓库：https://github.com/EYHN/hexo-helper-live2d
预览图：https://huaji8.top/post/live2d-plugin-2.0/
model下载：https://www.npmjs.com/search?q=%20live2d-widget-model

# 博客们：
- http://yuchen-lea.github.io/categories/hexo/
