---
title: Windows下Clion+Cygwin开发环境配置
date: 2018-03-27 16:49:40
categories:
- 教程
tags:
- Clion
- Cygwin
---

### 首先

下载 ***[Clion](https://www.jetbrains.com/clion)*** 和 ***[Cygwin](https://cygwin.com/install.html)*** 选择适合自己系统的版本 **(这里是Windows10 x64版本)**

### 安装 *Clion*

打开 ***.exe*** 文件，如图。更据安装向导选择自己喜欢的目录进行安装 **(这里是2017.2.4版本)**

![Clion_Instal](Windows下Clion+Cygwin开发环境配置\Clion_Install.PNG)

### 安装 *Cygwin*

打开 ***.exe*** 文件，然后点击 **下一步**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install0.PNG)

选择 ***Install from Internet*** ，然后点击 **下一步**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install1.PNG)

选择自己喜欢的目录安装 ***Cygwin*** ，选择为你当前计算机的所有用户或者仅是当前用户安装 ***Cygwin*** ，然后点击 **下一步**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install2.PNG)

选择 ***Use System Proxy Settings*** ，然后点击 **下一步**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install3.PNG)

选择一个镜像下载网址 **(这里选的默认)** ，然后点击 **下一步** 进入 **下载页面**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install4.PNG)

下载完成后，进入 ***Select Packages*(选择包) 页面**

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install5.PNG)

在搜索框中键入 ***gcc-core, gcc-g++, make, gdb* 和 *binutils*** ，搜索这些包并安装，然后点击 **下一步** ，确认你的包的选择之后再点击 **下一步** 进入 **下载安装包页面** 下载安装完成之后如图所示

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install6.PNG)

点击 **完成** 即可完成安装

安装完成后将 ***Cygwin*** 中 ***bin*** 目录添加到 ***path*** 环境变量

打开 ***CMD*** 键入 ***gcc -v*** 显示如图，验证完成安装

![Cygwin_Install](Windows下Clion+Cygwin开发环境配置\Cygwin_Install7.PNG)

### 配置 *Clion Toolchains*

首次安装 ***Clion*** 会跳转到 ***Toolchains*** 的设置页面，如果没有跳转则从 ***File > Settings > Build, Execution, Deployment*** 下找到 ***Toolchains***

![Clion_Config](Windows下Clion+Cygwin开发环境配置\Clion_Config.PNG)

将 ***Cygwin home*** 设为前面你安装 ***Cygwin*** 的目录，待底部全部显示符号 **✓** 则表示设置成功，点击 ***Apply*** 之后退出即可。