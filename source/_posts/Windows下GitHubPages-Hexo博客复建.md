---
title: Windows下GitHubPages+Hexo博客复建
date: 2018-04-02 18:48:33
tags:
- GitHubPages
- Hexo
categories:
- 教程
---

## 安装并配置 Git

**[Git](https://git-scm.com/)** 下载地址

下载完成之后安装 **Git**，之后配置 **Git**，在命令行输入

```shell
git config --global user.name "uglyservant"
git config --global user.email "uglyservant@yeah.net"
```

## 克隆远程库

添加本地 **Git** 权限，**Git Bash** 中输入

```shell
ssh-keygen -t rsa -C "uglyservant@yeah.net"
```

将 **SSH key** 添加到 **Github** 账户中

用文本编辑器打开 `id_rsa.pub` 文件，里面的信息即为 **SSH key**，将这些信息复制到 **GitHub** 的 `Add SSH key` 页面即可

在喜欢的目录下建立 `Blog` 目录，或者其它名字也可以，进入该目录打开 **Git Bash** 在命令行输入以下命令进行克隆

```shell
git clone git@github.com:uglyservant/uglyservant.github.io.git
```

## 安装 Hexo

下载 **[Nodejs](https://nodejs.org/en/)**，并安装

重新启动 **Git Bash**，进入本地仓库目录，输入

```shell
npm install hexo-cli -g
```

来安装 **Hexo**

输入

```shell
npm install
```

来完成相应的依赖安装

## 完成

接下来可以使用

```shell
hexo g -d
```

来发布新的文章

使用

```shell
git add . && commit -m "commit" && push
```

来同步远程库

