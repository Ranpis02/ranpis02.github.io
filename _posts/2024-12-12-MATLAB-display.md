---
title: 'MATLAB 基本配置'
date: 2024-12-12 00:49:31 +0800
categories: [MATLAB]
tags: [MATLAB]
---

## 切换语言

如果我们想要切换 MATLAB 的语言，我们可以到 <预设项>(perferences) -> <常规>(General) 中，下拉找到桌面语言并进行切换

## 切换 Dark Mode

MATLAB 2023a 版本及后续版本开始支持 Dark Mode，离线版安装方式如下：

1. 下载 [Support Software Downloader](https://www.mathworks.com/support/install/support-software-downloader.html)
2. 登录 MathWorks 账号，选择符合的版本，下载支持包 `New Desktop for MATLAB Tech Preview`
   > 下载路径尽量不要修改，否则可能会出现无法找到支持包的情况
   {: .prompt-tip}

进入 MATLAB 的安装目录，找到 `supportsoftware.exe`

```shell
cd DRIVE:\<MATLAB_PATH>\bin\win64
```

使用该安装器进行安装

```shell
install_supportsoftware.exe -archives <archives_path>
```
