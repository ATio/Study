---
layout: post
title: 网易前端微专业笔记之盒模型与布局
date: 2016-01-13 00:43:14
author: AwThink
description: 补一下网易前端微专业页面制作课程中盒模型与布局的视频，并做了简要摘记。
keywords: baidu-ife,百度Web前端技术学院,学习笔记,网易前端微专业,盒模型,布局
category: [致知录,ife]
tags: [baidu-ife,百度Web前端技术学院]
---

## display

### display:block  

- 3个特点是什么？
- 默认的块级元素有哪些？

### display:inline

- 3个特点是什么？
- 默认的行级元素有哪些？

### display:inline-block

- 4个特征
- 默认有哪些？from

### display:none vs visibility:hidden

- 不显示
- 不占地


## position

### z-index 栈

### pos-r

- 仍在文档流中，原位置**不会**被占
- 参照物是元素本身

### pos-a

- 默认宽度是内容宽度（那它还能设置宽高吗？可以。）
- 脱离文档流，原位置被占
- 参照物：最近一个已定位的元素，如果没有，则为根元素

### pos-f

可以视为 pos-a 的一种特殊形式。前两个特征一样，参照物为浏览器窗口。

### 小实例

做遮罩的时候宽高设成了 100% ，能不能通过把上右下左都设置成 0 来实现？  
实践结果：能。  
原理：如果一个定位的元素，没有设置宽高，但同时设置了 上/下、左/右 ，就会把元素给拉伸开，撑开。  
利用这一点，可以做一个上下固定，中间自适应的三行布局。


## float

- 默认宽度为内容宽度
- 脱离文档流
- 向指定的方向**一直**移动（直到被“挡住”）

- float元素在同一文档流中（所以两个`float:left`会并列，第二个被第一个挡住）
- float元素半脱离文档流：对元素来说，float元素脱离了文档流；但对内容来说，float元素还在文档流当中。

## flex

flex container、主轴、辅轴

- 在文档流中的直接子元素才是 flex item

### 方向

方向相关的属性：

- flex-direction：方向，行/列，反向行/反向列
- flex-wrap：换行方式
- flex-flow：上面两个的缩写
- order：排列顺序

### 弹性

弹性相关的属性

- flex-grow：分配剩余空间
- flex-shrinnk：有点像 flex-grow 的相反，当 flex item 超出容器，剩余空间为“负”的时，按什么比例去分配这些“负的”的空间。就是怎么去压缩了。
- flex-basis：设置 flex item 的初始宽/高。如果弹性元素按行排列，设置的就是宽，如果按列排列，设置的就是高。
- flex：以上三个的缩写。

### 对齐

- justify-content：设置主轴上的对齐方式。flex-start、flex-end、center、space-between、space-around，有点像text-align的作用，只不过弹性元素有轴的区别。
- align-items：设置辅轴方向上的对齐方式。类似vertical-align。前三个一样，后两个为 baseline、stretch
- align-self：设置单个flex item 在辅轴上的对齐方式。`align-items` 对容器内所有的弹性元素生效，而`aligh-self`对单个弹性元素起作用。
- align-content：设置辅轴方向上**行**的对齐方式。