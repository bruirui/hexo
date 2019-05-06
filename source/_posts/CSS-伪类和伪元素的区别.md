---
title: CSS 伪类和伪元素的区别
date: 2018-10-17 14:28:23
tags: css
---

> <font color="#456782">伪类</font>：会对现有的元素进行筛选
  <font color="#F8A131">伪元素</font>：会创造出不存在的新元素

<font color="#456782">伪类</font>总是以<font color="#456782">单冒号</font>开头，如：:last-child, :visited
<font color="#F8A131">伪元素</font>总是以<font color="#F8A131">双冒号</font>开头，如：::before, ::selection, ::first-line

在css2时代，<font color="#F8A131">伪元素</font>和<font color="#456782">伪类</font>都是以<font color="#456782">单冒号</font>(:)开头;在css2.1后，为了对<font color="#F8A131">伪元素</font>和<font color="#456782">伪类</font>加以区分，规定<font color="#456782">伪类</font>以<font color="#456782">单冒号</font>开头，而<font color="#F8A131">伪元素</font>改问<font color="#F8A131">双冒号</font>开头。

但为了向前兼容，浏览器也接受css2时代已经存在的<font color="#F8A131">伪元素</font>(:before,:after,:first-line,:first-letter)的<font color="#456782">单冒号</font>写法。但对于css2之后所有新增的<font color="#F8A131">伪元素</font>(如::selection),必须采用双冒号写法

IE9及以上版本支持双冒号写法，IE9之前版本需使用<font color="#456782">单冒号</font>写法兼容

<h6>参考: [https://www.renfei.org/blog/css-pseudo-class-and-pseudo-element.html](https://www.renfei.org/blog/css-pseudo-class-and-pseudo-element.html)