---
title: python链接sqlserver
date: 2020-06-05 15:08:55
tags:
 -python
 -sqlserver
categories: python
---
# python 连接sqlserver

## 安装pymssql

```cmd
pip install pymssql
```

<!--more-->

## 配置sa

1. 打开Microsoft SQL server management studio

2. 用windows身份认证登陆

3. 安全性->用户名->右击sa->属性

   ![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200523163508.png)

   是否允许连接到数据库引擎选择 授予

   登录名选择 启用

4. 问题： **pymssql.OperationalError: (20009, b'DB-Lib error message 20009, severity 9:\nUnable to connect: Adaptive Server is unavailable or does not exist (SZS\\SQLEXPRESS)\n')**　 解决

   按下win键搜索sqlserver配置管理器->sqlserver网络设置->选择需要使用的实例->TCP设置为启用

![](https://raw.githubusercontent.com/aidenz2020/FigureBed/master/20200523164450.png)

5. sqlserver配置管理器->sqlserver服务中重启你的实例

6. 在TCP/IP->IP地址记录下端口号

7. 运行以下代码

   ```python
   import pymssql
   
   conn = pymssql.connect(host='localhost',server='DESKTOP-AFG838O\SQLEXPRESS01', port='端口号', user='sa', password='密码', database='要连接的数据库')
   if conn:
       print("连接成功")
   conn.close()
   ```

   若显示连接成功则成功

## 利用pymssql对sqlserver进行基本操作

### 连接数据库

```python
import pymssql
def conn():
	conn = pymssql.connect(host='localhost',server='DESKTOP-AFG838O\SQLEXPRESS01', port='端口号', user='sa', password='密码', database='要连接的数据库')
	if conn:
    	print("连接成功")
    return conn
```

使用完执行conn.close()释放资源

### 查询操作

```python
def select():
    connect = conn()
    cursor = connect.cursor()   #创建游标对象，python中的sql语句都要通过游标进行操作
 	sql = "select * from database"
    row = cursor.fetchone()  #读取查询结果,
	while row:              #循环读取所有结果
		print(str(row[0])+' ' + str(row[1]) + ' ' + str(row[2]) + ' ' + str(row[3]))   #输出结果
		row = cursor.fetchone()
	cursor.close()
    connect.close()
```



### 更新操作

```python
def update():
    connect = conn()
    cursor = connect.cursor()
    sql = "update database set attribute = '****''"
    cursor.execute(sql)
    cursor.close()
    connect.close()
```

**注意s如果ql语句中有```'```,例如```update database set attribute = '####',则sql字符串应用双引号""扩起**

### 插入操作

```python
def insert(insertData):
    connect = conn()
    cursor = connect.cursor()
    sql = "insert into database (attribute1, attribute2, attribute3) values('%s', %d, '%s')"%(insertData[0],insertData[1], insertData[2]) #注意插入的数据类型要对应
    cursor.execute(sql)
    cursor.close()
    connect.close()
```

### 删除操作

```python
def delete(deleteData):
    connect = conn()
    cursor = connect.cursor()
    sql = "delete from table1 where attribute1 = '%s'"%(deleteData)
    cursor.execute(sql)
    cursor.close()
    connect.close()
```

