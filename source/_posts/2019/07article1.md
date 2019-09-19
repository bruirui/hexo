---
title: 前端测试：Karma+Mocha+PhantomJS
urlname: article1
date: 2019-07-22 16:50:18
tags: 工具
---

> 适用vue项目：Karma + Mocha + Chai + Vue Test Utils
>

### 一、对测试框架的理解（npm run lint执行过程：）

开启Karma运行环境(启动PhantomJS浏览器)，使得Mocha在PhantomJS浏览器环境下运行，去执行所有测试脚本。

1. 执行npm run lint命令
2. 开启Karma运行环境
3. 使用Mocha逐个测试用Chai断言写的测试用例
4. 在终端显示结果 
5. 如果测试成功，karma-coverage 会在 `./test/unit/coverage` 文件夹中生成测试覆盖率结果的网页

### 二、Karma

- [官网]: http://karma-runner.github.io/latest/index.html

- Karma是一个驱动测试的Runner。通过karma的配置文件集成测试框架, 断言库和浏览器。

- 用来组织和运行整个测试的工具，它能够将测试框架、断言库、测试浏览器、测试代码和被测试代码组织起来，并运行被测试代码进行测试。

- 为测试框架(Mocha)准备允许的环境，让测试在真正的浏览器里运行。

- 它是一个测试工具，能让你的代码在浏览器环境下测试。需要它的原因在于，你的代码可能是设计在浏览器端执行的，在node环境下测试可能有些bug暴露不出来；另外，浏览器有兼容问题，karma提供了手段让你的代码自动在多个浏览器（chrome，firefox，ie等）环境下运行。如果你的代码只会运行在node端，那么你不需要用karma。

- **为前端自动化测试提供了跨浏览器测试的能力**，可以自动在`Chrome`,`Firefox`,`IE`等主流浏览器依次跑完测试用例，同时也支持headless浏览器(如`phantomJs`)中运行测试用例。

- Karma支持的测试框架：Mocha、Jasmine、Qunit。

- 该工具在Vue中的主要作用是将项目运行在各种主流Web浏览器进行测试。

### 三、Mocha

- [官网]: https://mochajs.org/

- **Mocha是前端自动化测试框架**，测试框架需要解决**兼容不同风格断言库**，**测试用例分组**，**同步异步测试架构**，**生命周期钩子**等框架级的能力。

- Mocha是JavaScript的一种单元测试框架。既可以在浏览器环境下运行，也可以在Node.js环境下运行。使用Mocha，只需专注于编写单元测试用例本身，让mocha去自动运行所有测试脚本，并给出测试结果。

- 特点：

  - 既可以测试简单的JavaScript函数，又可以测试异步代码，因为异步是JavaScript的特性之一；
  - 可以自动运行所有测试，也可以只运行特定的测试；
  - 可以支持before、after、beforeEach和afterEach来编写初始化代码；

### 四、PhantomJS

- [官网]: https://phantomjs.org/

- 是一个基于 WebKit 的服务器端 JavaScript API，可以理解为无界面的浏览器。由于不渲染页面，网页的运行时间会大大缩短，该浏览器适用于测试。

- PhantomJS 可以用于 页面自动化(Page Automation) ， 网络监测(Network Monitoring) ， 网页截屏(Screen Capture) ，以及 无界面测试(Headless Website Testing) 等，简单来说就是通过js操作浏览器。

- **可测试类型**：性能测试、功能测试、界面测试

- 缺点：

  - 浏览器兼容。提供的是无界面的webkit内核浏览器，所以无法覆盖IE浏览器；
  - 设备兼容；



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

4. [前端测试简述及使用Karma/Mocha实现的集成测试栗子](https://blog.csdn.net/weixin_33805992/article/details/87988573)

5. [karma + mocha 简单入门](https://my.oschina.net/u/2510955/blog/910161)

    

