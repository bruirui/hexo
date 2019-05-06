---
title: 为什么用Object.prototype.toString.call(obj)检测对象类型?
date: 2018-10-11 16:47:03
tags: JavaScript
---

> [<font color="#456782">1.typeof是否能准确判断一个对象变量?</font>](#1)
  [<font color="#456782">2.instanceof原理?</font>](#2)
  [<font color="#456782">3.constructor原理?</font>](#3)
  [<font color="#456782">4.Object.prototype.toString.call()原理?</font>](#4)

javascript共有6种数据类型: 
  基本类型5种: undefined, string, number, boolean, null 
  引用类型1种: object
<h4 id="1">1. typeof是否能准确判断一个对象变量?</h4>不能，typeof检测返回结果有6种: undefined, string, number, boolean, object, function
<h4 id="2">2. instanceof原理?</h4>拓展：
    js对象都有一个__proto__属性(是实例的隐式原型，指向该对象的父对象的原型prototype)，显示的原型对象使用protoyoe，但Object.prototype.__proto__ = null;
<h5>instanceof用于判断一个实例是否属于某个对象。如：</h5>
```
  function Foo(){}
  var foo = new Foo()
  console.log(foo instanceof Foo) //true
  console.log(foo instanceof Function) //false
  console.log(foo instanceof Object) //true
  console.log(Foo instanceof Function) //true
  console.log(Foo instanceof Object) //true
```
<h4 id="3">3. constructor原理?</h4>
<h4 id="4">4. Object.prototype.toString.call()原理?</h4>