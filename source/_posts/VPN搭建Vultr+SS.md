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

<div style="text-align: center;">使用Vultr和SS搭建自己的VPN </div>
<!-- more -->

## 一

购买一个 **[Vultr](https://www.vultr.com/)** 的国外服务器

### 服务器位置

**Los Angeles**

### 操作系统

**CentOS 7 x64**

### 价格

我选的是 **$5/月**

## 二

连接服务器：

### 使用 Windows10 系统自带的 OpenSSH

打开系统命令行，输入：

```cmd
ssh username@host
```

`username` 为你登陆服务器的账户名称，`host` 为你的主机的 **IP** 地址

之后会让你输入账户的密码，输入正确即可登陆

## 三

下载 **SS** 服务器端

在命令行输入

```bash
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh
chmod +x shadowsocks-libev.sh
./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
```

在安装过程中配置自己喜欢的端口号和密码以及加密方式

启动 **BBR** 加速

```bash
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

验证是否启用 **BBR** 加速

```bash
lsmod | grep bbr
```

## 四

下载并配置 **SS** 客户端

**[SS 客户端下载地址](https://github.com/shadowsocks/shadowsocks-csharp/releases)**

