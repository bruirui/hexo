---
title: css常用&易忘属性
urlname: article1
date: 2018-09-03 09:58:27
tags: css
---

> [<font color="#456782">table: border-collapse</font>](#1)
  [<font color="#456782">-webkit-tap-highlight-color</font>](#2)
  [<font color="#456782"> -webkit-text-size-adjust</font>](#3)
  [<font color="#456782">-webkit-appearance</font>](#4)
  [<font color="#456782">-webkit-user-select</font>](#5)
  [<font color="#456782">-webkit-touch-callout</font>](#6)
  [<font color="#456782">outline</font>](#7)
  [<font color="#456782">文字截断</font>](#8)

<h3 id="1">1. border-collapse</h3>设置表格的边框是否被合并为一个单一的边框。
- separate,默认值。边框会被分开
- collapse,边框会合并为单一的边框。会忽略border-spacing和empty-cells属性
- inherit,从父元素继承border-collapse属性的值

<h3 id="2">2. -webkit-tap-highlight-color</h3>这个属性只用于iOS (iPhone和iPad),当用户点击一个链接或者通过Javascript定义的可点击元素的时候，它就会出现一个半透明的灰色背景。要重设这个表现，可以修改该属性值。
- color,颜色值
- transparent,透明值

<h3 id="3">3. -webkit-text-size-adjust</h3>
- none,禁用Webkit内核浏览器的文字大小调整功能

<h3 id="4">4. -webkit-appearance</h3>
- none,消除输入框和按钮的原生外观

<h3 id="5">5. -webkit-user-select</h3>
- none,禁止页面文字选择，此属性不继承

<h3 id="6">6. -webkit-touch-callout</h3>
- none,禁用长按页面时的弹出菜单(ios下有效)，img和a标签都要加。例：禁止在微信环境下长按保存图片

<h3 id="7">7. outline</h3>
- none,取消chrome下默认的文本框聚焦样式

<h3 id="8">8. 文字截断</h3>
- text-overflow
设置当文本溢出时表现
	- ellipsis,显示省略号代替被修剪的文本
	- clip,修剪文本
	- string,使用给定字符串来代替被修剪的文本
- white-space
设置如何处理元素内的空白
	- normal,默认值，空白被浏览器忽略
	- pre,空白会被浏览器保留
	- nowrap,文本不会换行，文本会在同一行上继续，直到遇到<br/>为止
	- pre-wrap,保留空白符序列，但是正常地进行换行
	- pre-line,合并空白符序列，但是保留换行符
	- inherit,从父元素继承
- word-break
规定自动换行的处理方法(可以让浏览器实现在任意位置的换行)
	- normal,默认值，使用浏览器默认的换行规则
	- break-all,允许在单词内换行
	- keep-all,只能在半角空格或连字符处换行
- -webkit-line-clamp: number
限制在一个块元素显示的文本的行数
该属性必须结合以下属性才能起作用：
	- display: -webkit-box; 将对象作为弹性伸缩盒子模型显示
	- -webkit-box-orient: vertical; 设置或检索伸缩盒对象的子元素的排列方式
	- text-overflow: ellipsis; 用省略号替换被截断的文本
	
- #### 单行截断:
```
	//设置文本不会换行，在同一行上继续绘制文本
	white-space: nowrap;
	//超过部分不显示
	overflow: hidden;
	//截断后用省略号替换被修剪的文本
	text-overflow: ellipsis;
```
- #### 多行截断:
```
	display: -webkit-box;
	//规定超过两行的部分截断
	-webkit-line-clamp: 2;
	-webkit-box-orient: vertical;
	//截断后用省略号替换被修剪的文本
	text-overflow: ellipsis; 
	//超过部分不显示
	overflow : hidden;
	word-break: break-all;
```

​	




