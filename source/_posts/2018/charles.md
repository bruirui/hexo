---
title: 抓包-IOS手机连接Charles
urlname: article6
date: 2018-08-27 19:01:35
tags: 工具
---

>工具：Charles、ios手机

1. Charles软件：Proxy->Proxy Settings ->勾选Enable transparent HTTP proxying
2. 找到电脑ip，iphone上设置代理(端口号一般为8888)
3. 手机设置完成后，charles会弹出允许提示框
4. 手机安装证书：charles菜单 Help->SSL Proxying -> Install Charles Root Certificate on a Mobil …，弹出对话框，显示证书地址。在手机safari输入地址进入就会安装证书
（安装的证书可以在 iphone设置->通用->描述文件查看到）
5. 手机信任证书：iphone设置->关于手机->证书信任设置(最底部)->勾选刚刚安装的证书
