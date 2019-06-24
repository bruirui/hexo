---
title: NVM | NRM | NPM
urlname: article1
date: 2019-06-24 10:50:10
tags: 工具
---

### 一、NVM
node版本管理器 (Node Version Manager)

常用命令：

```bash
nvm ls              ---查看当前机器已经安装的所有node版本
nvm install 9.11.0  ---安装v9.11.0版本
nvm use 9.11.0      ---切换node版本为v9.11.0
nvm current         ---查看当前使用的node版本
nvm ls-remote       ---查看当前发布的所有node版本

nvm run 9.11.0 app.js     ---用v9.11.0的node版本运行app.js
nvm alias default 9.11.0  ---设置shell默认使用的node版本为v9.11.0
nvm alias default node    ---shell始终默认使用最新的node版本

nvm --help 					---查看nvm命令行
```



### 二、NRM

npm镜像管理工具(npm registry manager)

如：有时国外资源太慢，可以用nrm切换镜像源

常用命令：

```bash
#安装nrm
npm install -g nrm
#查看当前所有可用的源
nrm ls
#查看当前再用的源
nrm current
#切换到taobao
nrm use taobao
#添加源 add <registry> <url> [home]
nrm add taobao https://registry.npm.taobao.org/

#查看nrm命令行
nrm -h
```



### 三、NPM

包管理工具

```bash
#npm升级
npm install npm -g
#切换为淘宝镜像源
npm install -g cnpm --registry=https://registry.npm.taobao.org
#使用npm安装模块
npm install <Module Name> ---本地安装
npm isntall <Module Name> ---全局安装
```

提升：发布npm包&自测使用，熟悉npm包发布流程&封装组件

