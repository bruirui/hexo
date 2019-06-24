---
title: 封装vue组件并使用npm发布
urlname: article1
date: 2019-05-06 14:28:08
tags: 工具
---

### 一、封装vue组件

参考链接：https://www.cnblogs.com/web-chuanfa/p/9304752.html



#### Vue.component()

- 注册全局组件

- 第一个参数：自定义元素名称

- 第二个参数：将要注册的vue组件

  ```javascript
  import Vue from 'vue'
  import Loading from './Loading.vue'
  Vue.component('loading', Loading);
  ```

#### Vue.use()

- 注册插件
- 接收一个参数：该参数必须有install方法，Vue.use函数内部会调用参数的install方法
- Vue.use()方法内部会检测插件的installed属性，从而避免重复注册插件
- 插件的install()方法有2个参数，第一个参数是Vue，第二个参数是配置项options
- 在install()方法内部可以添加全局方法、属性、全局指令、mixin混入、添加实例方法、使用Vue.component()注册组件

### 二、发布到npm

