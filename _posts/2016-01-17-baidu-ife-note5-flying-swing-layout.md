---
layout: post
title: 双飞翼布局
date: 2016-01-17 20:35:25
author: AwThink
description: 慕课网上一个介绍双飞翼布局的帖子，第一次看，粗略摘记。
keywords: baidu-ife,百度Web前端技术学院,双飞翼,布局
category: [致知录,ife]
tags: [baidu-ife,百度Web前端技术学院,双飞翼布局,栅格化布局]
---

# 双飞翼

## 布局技术总结

1. 浮动 float
1. 负边距 negative margin
1. 相对定位 relative position

以上三个是最基本的布局技术。通过巧妙的组合，能够实现各种实现方案。

## 例子

> 利用浮动元素的负边距来定位

`margin-left:-100%;`、`margin-left:-230px;`
为什么负的`margin`有这效果？原理是什么？实现方式是什么？

里面一共 5 个例子，一步一步深入。挨个看过去就好了。  
里面有一句话：

> 这个布局的实现思路是，先把最重要的身体部分放好，然后再将翅膀移动到适当的地方。

结合例子5 去看这句话。可以发现，在例5中最左边，`sub`没有充满`bd`的高度，于是我们能够看到，实际上`main`是占满整行的，即`.main {width: 100%;}`，只不过当侧边栏浮动+定位过来之后，让人以为`main`向右移动了一样。  
大概这便是“先把最重要的身体部分放好”的意思吧。


此外文末另有一套栅格化布局系统，需要抽时间研究一下源代码。

## 学习资料

[双飞翼布局介绍-始于淘宝UED](http://www.imooc.com/wenda/detail/254035)
[利用双飞翼实现的栅格化布局系统](http://www.dqqd.me/avatar/fly/grids_test1.html)