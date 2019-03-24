---
title: VPN搭建Vultr+SS
date: 2019-02-26 21:58:05
tags:
- VPN
- Vultr
- SS
categories:
- 教程
---

## 一

购买一个***[Vultr](https://www.vultr.com/)***的国外服务器

### 服务器位置

***Los Angeles***

### 操作系统

***CentOS 7 x64***

### 价格

我选的是$5/月

## 二

连接服务器

### 下载并运行*Putty*

在***Putty***中的***Session***将服务器的***IP***地址填好

在***Putty***中的***Data***将服务器的用户名填好:***root***

点击***open***

## 三

下载***SS***服务器端

在命令行输入

```bash
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh
chmod +x shadowsocks-libev.sh
./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
```

在安装过程中配置自己喜欢的端口号和密码以及加密方式

启动***BBR***加速

```bash
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

验证是否启用***BBR***加速

```bash
lsmod | grep bbr
```

## 四

下载并配置***SS***客户端

[***SS***客户端下载地址](https://github.com/shadowsocks/shadowsocks-csharp/releases)

