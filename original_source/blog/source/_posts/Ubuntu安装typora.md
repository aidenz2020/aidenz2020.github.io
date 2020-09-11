---
title: Ubuntu安装typora
date: 2020-06-05 15:47:24
tags:
 -ubuntu
 -typora
categories: ubuntu
---
## Ubuntu安装typora

```bash
# optional, but recommended
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE

# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt update

# install typora
sudo apt install typora
```

