---
title: 'scoop 安装 vscode 后扩展无法使用'
date: 2025-01-05 13:04:10 +0800
categories: [bug]
tags: [scoop, vscode]
---

## 问题描述

在使用 `scoop` 安装 `vscode` 以基于 `vscode` 修改的软件，例如 `cursor` 等会出现扩展无法安装的现象。

## 解决方法

一般而言，这是由于 `vscode` 同步账户中的扩展太多或者出现非 ASCII 字符，导致 `extension.json` 出现错误。我们进入到 `DRIVE:\<VSCODE_PATH>\current\data\extensions` 目录中，找到 `extension.json`，对 `.json` 文件出现错误的位置进行纠正，例如缺少引号等。

![Snipaste_2025-01-01_18-14-38](https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/Snipaste_2025-01-01_18-14-38.jpg)

除了上述解决方法外，也可以先不使用 `scoop` 安装，直接安装 `vscode`，然后将里面的 `extension.json` 复制拷贝到 `scoop` 安装的 `vscode` 目录下相应位置

![image-20250105133128389](https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/image-20250105133128389.png)
