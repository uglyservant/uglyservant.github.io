---
title: Windows10卸载自带应用
date: 2018-04-02 18:52:39
tags:
- Windows10
categories:
- 教程
---

<center>烦人的巨硬操作系统自带的应用</center>

<!-- more -->

## 进入终端

以 **管理员** 的身份打开 **Windows10** 的 **PowerShell** 或者 **CMD** 命令行
![PowerShell](PowerShell.PNG)

## 删除应用

首先键入 **Get-AppxPackage | Select Name, PackageFullName** 得到所有内置的应用

![Get_App](Get_Apps.PNG)

之后键入 **Get-AppxPackage \*AppName\* | Remove-AppxPackage** 来删除你不需要的应用

**AppName** 就是你想要删除的应用的名称，可以从上一步中列出来的应用清单中复制过来

