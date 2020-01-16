---
title: MySQL8.0.16(ZIP包) 安装和配置
date: 2020-01-16 10:24:16
tags:
- MySQL
categories:
- 教程
---

<center>MySQL8.0.16 ZIP 包安装和配置</center>

<!-- more -->

## 一、安装MySQL

解压ZIP包至自定义目录，如`C:\Program Files\MySQL8.0.16\`，在自定义目录下创建`MySQL`配置文件`my.ini`(可选)。

`MySQL`配置文件`my.ini`内容如下：

```
[mysqld]
# 设置3306端口
port=3306

# 设置mysql的安装目录
basedir=C:\Program Files\MySQL

# 设置mysql数据库的数据的存放目录
datadir=E:\database\MySQL\Data

# 允许最大连接数
max_connections=200

# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10

# 服务端使用的字符集默认为UTF8
character-set-server=utf8

# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB

# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password

[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8
```

## 二、初始化MySQL

打开`CMD`，进入`C:\Program Files\MySQL8.0.16\bin\`目录下，键入如下命令(二选一)

- `mysqld --initialize --console`(使用`root`用户和`随机`密码初始化数据库，并打印该密码至控制台)
- `mysqld --initialize-insecure`(使用`root`用户和`空`密码初始化数据库)

## 三、更改MySQL登陆密码

先将`C:\Program Files\MySQL8.0.16\bin\`添加到系统环境变量中。
打开`CMD`，输入`mysql -u root -p`，对话框提示输入密码，有则填入密码，无则直接回车。
进入`mysql`对话框，输入

```SQL
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';
```

下次登陆使用新密码即可。