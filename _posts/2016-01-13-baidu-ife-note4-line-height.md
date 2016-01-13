---
layout: post
title: 学习笔记之 line-height
date: 2016-01-13 21:31:14
author: AwThink
description: 
keywords: baidu-ife,百度Web前端技术学院,学习笔记,line-height,CSS
category: [致知录,ife]
tags: [baidu-ife,百度Web前端技术学院]
---

## line-height

5 种定义方式：百分比、px、数字、继承、normal

与 font 缩写：`body{font:100%/normal  arial;} `

### 百分比

	body{
		font-size:16px;
		line-height:120%;
	}

line-height = 16 * 120%
			= 19.2px

- 这个值会被后代元素继承
- 所有继承该值的元素会忽略自身的 font-size ，直接使用该 line-height 值
- line-height 不会随着相关的 font-size 做相应的比例缩放

### px值

和百分比一样

### normal

- 继承元素**不会**忽略自身 font-size ，使用基于自身 font-size 值计算出来的line-height
- line-height 会随相关 font-size 做相应的比例缩放

### 数字

- 继承元素基于 font-size 计算 line-height
- line-height 会缩放

一般来说，行高设为**纯数字**最为理想。

line-height 和 font-size 的差别举例：  
`font-size:16px` `line-height:20px` 相差 4px，即为行间距。把这个行间距拆分成两半，即半行间距，分别应用在`content area`的顶部和底部。  
但有时候情况不会这么理想。这些复杂的情况现在理解不深，留待以后再慢慢体会。