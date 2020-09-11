---
title: 多电脑维护hexo博客
date: 2020-09-11 15:41:07
tags:
 -hexo
 -github
 -git
categories: hexo
---

# 多电脑维护hexo博客

## 起因

之前闲的无聊在电脑装了ubuntu+win10的双系统，并在ubuntu系统上搭建了hexo+github的博客，现在感觉双系统真的不是太有用，因为ubuntu装到了机械硬盘上所以运行速度也不是很快，没有比虚拟机快多少，每次还要切换系统还要开关机，不如用虚拟机用的舒服。

所以现在想写个博客还要先把文件先传到ubuntu系统上，在通过ubuntu发布，很不方便，于是就想在win10和ubuntu两个系统上一起维护hexo博客。

windows系统和ubuntu系统应该都可以使用这个方法，大同小异。



<!--more-->



## 思路

在github上新建一个名为hexo的分支，master存放关于静态页面的文件，hexo的源文件。

## 搭建步骤

### 原电脑

- 安装git（既然hexo都部署好了，git也应该安装好了吧，不会真的有人没安装好git吧，不会吧不会吧）
- 登录github，在xxxx.github.io仓库新建一个branch，名为hexo，并将hexo分支设置为默认分支。

- 新建一个文件夹，命名自定，这里我取名为```hexo_blog``` ,终端或git bash键入```git init```，将仓库clone到该文件夹下，```git clone git@github.com.xxxx.git``` ,
- clone之后进入xxxx.github.io文件夹下， 查看一下分支```git branch``` ,应该为第二步新建的hexo分支，将本地的源文件copy到xxxx.github.io文件夹下，```cp -r xxxx/blog xxxxxx/xxxx.github.io```,进入复制后的源文件夹下，```cd blog```,
- 因为我这里使用的是next主题，要删除next主题文件夹下的```.git```文件，因为提交时不允许一个仓库内有里另一个仓库，```cd themes/next/```,```rm -rf .git```,因为提交时主题文件夹里的内容可能不会被提交上去，可以直接将themes文件夹打包，```rar -a theme themes/```,
- 将xxx.github.io提交到github的hexo分支上，在xxxx.github.io文件夹下，```git add .```,```git commit -m "commit source"```,```git push```

## 新电脑

- 安装node.js,npm,cnpm，git，hexo等，配置ssh key，像第一次部署hexo一样配置环境。
- 新建文件夹，进入文件夹后```git init```,clone仓库```git clone git@github.com.xxxxx.git```
- 进入xxxx.github.io\blog 文件夹后执行```npm install ```,``` npm install hexo-deployer-git ```,在blog文件夹下执行```hexo d```,如果可以通过```localhost:4000```查看网页，则成功。

# 日常维护

- 在日常更新时，首先要保持本地与远端保持一致，```git pull hexo```,更新好博客后，```hexo d```,```git add . ```,```git commit -m " "```,```git push```.

## reference

(https://www.dazhuanlan.com/2019/09/25/5d8adf4204ed4/?__cf_chl_jschl_tk__=edd065a2592374604c9747c630d2092cabd8d871-1599812832-0-AWLlZUG7hxIfywhP7SI-j47r8OjgocSO0iiUToA-RzjWWWEKEe-QnN-4Sfc5vLaxwejSgmwsNYMDsAe0KJU5hZ5I8fXM6CLSItUPfqE5B976-nKn8060LboK67QJ62LP0LzkzXNKYgGTa_S1Wbt2LDU6FI2NfVEkEQK_pSUof1uUOGbGLbbJNmSz0Mwi94Upt0NrfcF35vz6XIWXW5R_fGRjrpk0LRbkKd3YkKyNrJ_KR3tstLmaFnU7dnPxcL3B3HrHKhT0ifeAjGOpux9Lk-zRWorHpFOTWh5kubmufxabS_MaC3YK6uwihbSx019z0w)[]

(https://www.zhihu.com/question/21193762)[]