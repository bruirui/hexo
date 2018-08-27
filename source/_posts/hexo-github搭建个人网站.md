---
title: hexo+github搭建个人网站
date: 2018-08-22 17:35:01
tags: Hexo
---

>该文章参考: [使用hexo+github搭建免费个人博客详细教程](http://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html)

---
前期准备工作(macOS系统)
- github账号
- 安装好nodejs,npm,git

### 步骤

#### 一、创建github仓库
新建一个名为 用户名.github.io的仓库，比如说，我的github用户名为bruirui,那么就新建bruirui.github.io的仓库(必须是本人用户名，其他名称无效)。这样我的网站访问地址就是[https://bruirui.github.io](https://bruirui.github.io)

#### 二、自定义访问域名(我没有设置~略过)
使用默认的域名也是可以访问的，自定义只是为了实现个性化。

#### 三、hexo使用
- 安装hexo
``` bash
$ npm install -g hexo
```
- 初始化
在电脑上创建文件夹hexo,用于存放代码
``` bash
$ cd hexo
$ hexo init
```
- 生成&启动服务
hexo s 是启动本地预览服务，浏览器访问[http://localhost:4000](http://localhost:4000)就可以看到内容
``` bash
$ hexo g	#生成 hexo generate
$ hexo s 	#启动服务 hexo server
```
- 修改主题
个人选择的主题：hexo-theme-yilia
首先下载这个主题(还是在hexo文件夹下执行命令:)
``` bash
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```
修改_config.yml中的theme: landscape改为theme: yilia，然后重新执行hexo g来重新生成
- 上传到github
配置_config.yml中有关deploy的部分：
``` bash
$ deploy:
$  type: git
$  repository: https://github.com/bruirui/bruirui.github.io.git(第一步创建的git仓库地址)
```
安装一个插件：
``` bash
$ npm install hexo-deployer-git --save
```
然后输入 hexo d 命令,即可把代码部署到git上(注：这里存放的代码时hexo g生成后的代码)：
``` bash
$ hexo d 	#hexo deploy
```
<font color="red">注意：当再次提交代码到git仓库时，使用以下命令:<font>
``` bash
$ hexo d -g 	#在部署代码前会先进行生成代码 hexo deploy -generate
```
- 将代码保存到git仓库(hexo d保存的代码时hexo g生成的代码)
在git上新建一个仓库如：hexo(记住仓库地址:https://github.com/bruirui/hexo.git)
在本地hexo文件夹下执行以下命令:
``` bash
$ git init
$ git add -A
$ git commit -m"init"
$ git remote add origin https://github.com/bruirui/hexo.git
$ git puhs -u origin master
```
若提示需要先git pull,且git pull并不成功时，可执行以下命令<font color="red">(该命令会删除远程git仓库所有代码,提交本地代码):</font>
``` bash
$ git push -u origin master -f
```

### 新写一篇文章
- 定位到hexo目录,执行命令：
``` bash
$ hexo new "hexo+github搭建个人网站"
```
- 执行命令后结果：hexo会帮我们在_posts下生成相关md文件：
![执行结果.png](../../../../resource/hexoNew.png "执行结果")
- 现在只需要打开该文件就可以编辑文章了

### 额外补充---常用hexo命令
常见命令
``` bash
$ hexo new "postName" #新建文章
$ hexo new page "pageName" #新建页面
$ hexo generate #生成静态页面至public目录
$ hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
$ hexo deploy #部署到GitHub
$ hexo help  # 查看帮助
$ hexo version  #查看Hexo的版本
```
缩写
``` bash
$ hexo n == hexo new
$ hexo g == hexo generate
$ hexo s == hexo server
$ hexo d == hexo deploy
```
组合命令
``` bash
$ hexo s -g #生成并本地预览
$ hexo d -g #生成并上传
```
