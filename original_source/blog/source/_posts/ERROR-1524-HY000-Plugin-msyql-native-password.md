---
title: ERROR 1524 (HY000) Plugin '''msyql_native_password'''
date: 2020-06-05 15:37:45
tags:
 -mysql
 -ubuntu
categories: mysql
---
# ERROR 1524 (HY000): Plugin 'msyql_native_password' is not loaded

1. 在/etc/mysql/my.cnf中添加

```
[mysqld]
skip-grant-tables
```

<!--more-->

2. 重启mysql

```bash
service mysql restart
```

3. 重新登录```sudo mysql``` 

   输入以下命令

```mysql
select user, plugin from mysql.user
update mysql.user set authentication_string=PASSWORD('你的密码'), plugin='mysql_native_plugin' where user='root';
```

4. 退出 重新登录

```mysql
exit
mysql -u root -p
```

# ERROR 1698 (28000): Access denied for user 'root'@'localhost'

## 原因

没有创建root用户

## 解决

```bash
 sudo vim /etc/mysql/debian.cnf
```

使用文件中的user和password登录

创建root用户
