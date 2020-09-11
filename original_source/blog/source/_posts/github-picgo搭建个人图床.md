---
title: github+picgo搭建个人图床
date: 2020-06-05 15:09:35
tags:
 -github
 -图床
 -picGo
categories:
---
# github+picGo搭建个人图床

## 0. 注册github账号、下载picGo，

（可以在百度网盘中下载[https://pan.baidu.com/s/177K6Dsu4gwW6C4ooxsA9SQ]()  提取码：ltwr

 也可在[ https://github.com/Molunerfinn/PicGo/releases ](官网)下载）

## 1. 登陆github 新建仓库

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/QQ%E6%88%AA%E5%9B%BE20200512205754.png)

注意权限一定是public

<!--more-->


## 2. 在github中点击settings->Developer settings->Persional access tokens->Generate new token 键入note（随便填），然后点击repo

![1589288644190](C:\Users\张镇\AppData\Roaming\Typora\typora-user-images\1589288644190.png)

拖到网页最下面，点击Generate token 这样你就看见一串token![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/QQ%E6%88%AA%E5%9B%BE20200512210624.png)

记得复制下来并保存

## 3. 打开picGo 选择图床设置->github图床设置，键入设定仓库名（username/repo)、设定分支名（master）、设定token（步骤三中复制的token）点击确定，

## 4. 上传图片即可得到markdown的链接

**上传图片的名字尽量用英文或英文+数字，不用中文，否则会出现上传不了的情况**

