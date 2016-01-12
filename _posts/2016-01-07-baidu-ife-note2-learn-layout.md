---
layout: post
title: 《学习CSS布局》笔记
date: 2016-01-07 23:05:10
author: AwThink
description: 
keywords: baidu-ife,百度Web前端技术学院,学习笔记,学习CSS布局
category: [致知录,ife]
tags: [baidu-ife,百度Web前端技术学院,CSS]
---

[学习 CSS 布局](http://zh.learnlayout.com/no-layout.html)

## 没有布局时
在没有布局的网页里，内容会随着浏览器窗口变化，这会带来一个问题，当浏览器最大化的时候，内容从左到右贯穿，阅读时视觉焦点要移动很大一段距离，也就是你的头要不停的左右来回地动，十分不便。

由此引出`display`

## display

`display`是 CSS 中最重要的用于控制布局的属性。每一个元素都有一个默认的 display 值。

- block
- inline
- none

`display:none;` 和 `visibility: hidden;` 的区别：把 display 设置成 none 不会保留元素本该显示的空间，但是 visibility: hidden; 还会保留。 

## margin:auto;

设置块级元素的 width 可以阻止它从左到右撑满容器。然后你就可以设置左右外边距为 auto 来使其**水平居中**。元素会占据你所指定的宽度，然后剩余的宽度会一分为二成为左右外边距。 

当浏览器窗口小于 width 值时会出现水平滚动条。

### 改进方案

使用 `max-width` 替代 `width` 

	#main {
	  max-width: 600px;
	  margin: 0 auto; 
	}

这样就不会出现滚动条了吗？  
应该是在一定范围内不会出现，如果浏览器窗口足够小，比如比 main 的内容占的空间还要小，可能就会出现滚动条了吧。

## 盒模型

### box-sizing

`box-sizing: border-box;`

	* {
	  -webkit-box-sizing: border-box;
	     -moz-box-sizing: border-box;
	          box-sizing: border-box;
	}

这样可以确保所有的元素都会用这种更直观的方式排版。 

### position

> 其他的元素则不会调整位置来弥补它偏离后剩下的空隙。 

这句话是什么意思？

- **static**
- **relative**
- **fixed**
	- 一个固定定位元素不会保留它原本在页面应有的空隙。  
	- 移动浏览器对 fixed 的支持很差。
- **absolute**
	- 相对于最近的“positioned”祖先元素定位，如果没有，就相对于文档的 body 元素定位。

#### position 例子

这里 position 的例子为我们带来了一个“左栏定宽，右侧自适应布局”的方案：

- 最外层包裹层设置`position: relative;`；
- 左栏设置绝对定位，`left:0;`，加一个固定宽度；
- 右侧设一个 margin-left ，留个左栏，不设定位。

这样就完成了一个左侧固定宽度，右侧自适应的布局。  
缺点：当右侧内容较少撑不起高度，导致最外层包裹层高度小于左侧高度时，左侧会溢出外层包裹层。

### float

### 清除浮动

关于 float 和 clear 和 clearfix hack 的内容较少。可以配合 task1 任务6 里的参考资料一起看。

[Which method of ‘clearfix’ is best?](http://stackoverflow.com/questions/211383/which-method-of-clearfix-is-best)

### 浮动布局例子

完全使用`float`来实现页面的布局是很常见的。

前面用 position 实现的“左栏定宽，右侧自适应布局”的方案，也可以用 float 实现。

至此，**任务6 的第一个问题得到解决。**  
思考：该问题是一个布局问题，那么，布局和什么有关？→ CSS ，CSS 中有哪些和布局有关的属性？

看到第 13 页

### 百分比宽度

百分比相对于包含块，即，它相对于它的父元素。  
百分比对图片很有用。

百分比宽度能用来做布局。  

布局的方式很多，你应该根据内容来选择最适合的一种。

### 媒体查询

介绍相对较少，但给了一个 [MDN CSS媒体查询](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Media_queries)的链接。

### inline-block

对比了 float 和 inline-block，使用 inline-block 会更简单。

inline-block 也能做布局。

- vertical-align 属性会影响到 inline-block 元素，你可能会把它的值设置为 top
- 你需要设置每一列的宽度
- 如果HTML源代码中元素之间有空格，那么列与列之间会产生空隙

最后这一点，貌似曾经在 QQ群 里看到有人踩过这个坑，当时死活找不到原因，因为没人能够想得到代码里的空格也会影响到。

### column

以前很少接触到这个属性。

	.three-column {
	  padding: 1em;
	  -moz-column-count: 3;
	  -moz-column-gap: 1em;
	  -webkit-column-count: 3;
	  -webkit-column-gap: 1em;
	  column-count: 3;
	  column-gap: 1em;
	}

### flexbox

使用 flexbox 需要注意几点：

1. 规范变动频繁，需要注意
2. 网上不少 flexbox 的资料是过时的，需要注意辨别

又一个左定宽右自适应的布局方案：

	.container {
	  display: -webkit-flex;
	  display: flex;
	}
	nav {
	  width: 200px;
	}
	.flex-column {
	  -webkit-flex: 1;
	          flex: 1;
	}

所以是不是有必要回顾一下上面的所有布局方式，看看常见的布局到底有多少种方法可以实现？  

1. 一栏
	- 一栏居中，定 max-width 
2. 两栏
	- 左定宽，右适应
3. 三栏
	- 左右定，中间自适应

flexbox 能实现左右、上下均居中的布局！
	
	.vertical-container {
	  height: 300px;
	  display: -webkit-flex;
	  display:         flex;
	  -webkit-align-items: center;
	          align-items: center;
	  -webkit-justify-content: center;
	          justify-content: center;
	}