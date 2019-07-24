---
title: 前端测试：Karma+Mocha+PhantomJS
urlname: article1
date: 2019-07-22 16:50:18
tags: 工具
---

> Karma是一个基于Node.js的JavaScript测试执行过程管理工具（Test Runner）。
>
> Mocha是一个测试框架，在vue-cli中配合chai断言库实现单元测试。
>

### 一、对测试框架的理解（npm run lint执行过程：）

1. 执行npm run lint命令
2. 开启Karma运行环境
3. 使用Mocha逐个测试用Chai断言写的测试用例
4. 在终端显示结果 
5. 如果测试成功，karma-coverage 会在 `./test/unit/coverage` 文件夹中生成测试覆盖率结果的网页

### 二、Karma

- [官网]: http://karma-runner.github.io/latest/index.html

- Karma是一个驱动测试的Runner。

- 为测试框架(Mocha)准备允许的环境，让测试在真正的浏览器里运行。

- **为前端自动化测试提供了跨浏览器测试的能力**，可以自动在`Chrome`,`Firefox`,`IE`等主流浏览器依次跑完测试用例，同时也支持headless浏览器(入`phantomJs`)中运行测试用例。

- Karma支持的测试框架：Mocha、Jasmine、Qunit。

### 三、Mocha

- [官网]: https://mochajs.org/

- **Mocha是前端自动化测试框架**，测试框架需要解决**兼容不同风格断言库**，**测试用例分组**，**同步异步测试架构**，**生命周期钩子**等框架级的能力。

### 四、PhantomJS

- [官网]: https://phantomjs.org/

- 是一个基于 WebKit 的服务器端 JavaScript API，可以理解为无界面的浏览器。

- 由于不渲染页面，网页的运行时间会大大缩短，该浏览器适用于测试。

- PhantomJS 可以用于 页面自动化(Page Automation) ， 网络监测(Network Monitoring) ， 网页截屏(Screen Capture) ，以及 无界面测试(Headless Website Testing) 等,简单来说就是通过js操作浏览器。

- **可测试类型**：性能测试、功能测试、界面测试

- 缺点1：浏览器兼容。提供的是无界面的webkit内核浏览器，所以无法覆盖IE浏览器。

- 缺点2：设备兼容。



#### [拓展-浏览器内核]

- Trident内核：IE、傲游、世界之窗浏览器、Avant、腾讯TT、Sleipnir、GOSURF、GreenBrowser和KKman
- Gecko内核：Firefox
- Presto内核：Opera前内核
- Webkit内核：Safari内核、Chrome内核原型
- Blink内核：Chrome（28及往后版本）、Opera（15及往后版本）、Yandex浏览器

##### 【参考文章】：

1. [js单元测试实践](https://myronliu.com/2016/08/10/%E5%89%8D%E7%AB%AF%E5%B7%A5%E5%85%B7/javascript_unit/)

2. [基于Karma+Mocha+Chai的单元测试](https://blog.51cto.com/13869008/2175983)

3. [搭建 vue2 单元测试环境(karma+mocha+webpack3)](https://www.cnblogs.com/nxmin/p/9077187.html)

   

