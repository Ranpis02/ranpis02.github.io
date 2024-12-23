---
title: 'MATLAB 基本配置'
date: 2024-12-12 00:49:31 +0800
categories: [tools]
tags: [dev, matlab]
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

## 解决 BUG

我们在安装 `New Desktop for MATLAB Tech Preview` 后发现语言无法切换

- 原因： `New Desktop for MATLAB Tech Preview` 下载安装时会根据当前 Windows 系统语言决定安装的是哪一个语言的界面且后续无法更改
- 解决方案：**需要将插件卸载后更换系统语言然后再重新安装插件**，此时界面语言才会换成我们想要的

## 小技巧

如何加快 MATLAB 的启动速度？

由于 MATLAB 搜索 license 需要一定的时间，因此我们可以直接在 `.exe` 执行程序中执行 license 的位置，即在执行程序后面添加

```shell
-c <license_path>
```

其中 license 文件的位置一般在 `DRIVE:\<MATLAB_PATH>\licenses` 目录下
