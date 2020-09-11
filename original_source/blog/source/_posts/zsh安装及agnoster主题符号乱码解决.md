---
title: zsh安装及agnoster主题符号乱码解决
date: 2020-06-05 15:47:36
tags:
 -zsh主题

categories: zsh主题
---
## zsh安装及agnoster主题符号乱码解决

### 下载zsh

安装zsh

```bash
sudo apt-get install zsh
```

<!--more-->

安装oh-my-zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

然后使用zsh替换bash

```bash
chsh -s `which zsh`
```

### 修改zsh主题

通过修改~/.zshrc进行配置

```bash
sudo vim ~/.zshrc
```

找到```ZSH_THEME``` 后将其改为

```bash
ZSH_THEME="agnoster"
```

下载powerline字体

进入网址[https://github.com/powerline/fonts]()clone仓库

运行./install.sh安装字体




在终端找到编辑->首选项->配置文件->自定义字体，找到```UbuntuMono derivative Powerline Regular``` 

重启终端

