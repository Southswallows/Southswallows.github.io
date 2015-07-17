---
layout: post
category: 技术
title: Github上建立项目web
tags: web
---

>只要在GitHub上建立一个**名为github账户名的仓库**
>就能通过 `http://[用户名].github.com/`来访问这个项目的网页内容，即`Github pages`的使用。

###[Github pages用法请点击](https://pages.github.com/)

##现在要介绍的是，如何建立项目展示的WEB

>我们希望的是通过`http://[用户名].github.com/[项目名]`访问到的项目演示页面。

###1. 在Github上建立一个新的仓库（假设名字为resume）

###2. 需要在这个仓库下载建立一个名为`gh-pages`的分支

###3. 在`master分支`编写内容，然后push到远程仓库，同时也要对`gh-pages分支`进行push	
		git push origin master：master
		git push origin master:gh-pages
		两行代码意思，将本地的master分支分别push到远程的
		master分支和gh—pages分支

>如果觉得要多维护一个分支还是挺费事的。也可以只维护一个分支然后够生成演示页面

>把默认的master分支删除，把gh-pages当成主分支。

