---
title: '打开 UE 项目显示 The following modules are missing or built with a different engine version'
date: 2025-02-21 11:33:08 +0800
categories: [bug]
tags: [unreal]
---

## 问题描述

使用 Unreal Engine 4.27 打开别人的 UE 项目时出现 `The following modules are missing or built with a different engine version` 报错警告

## 解决方法

参考下表，根据自己的 UE 版本选择合适的 VS 版本

| Unreal Engine Version | Visual Studio Version       |
| --------------------- | --------------------------- |
| **5.1 or Later**      | VS 2019 (Default) / VS 2022 |
| **4.25 to 5.0**       | VS 2019 (Default)           |

> VS 支持同时安装多个版本，但是要保证从低版本开始安装，然后借助 `Visual Studio Installer` 安装其他高版本的 VS，如果之前电脑上已经安装了高版本 VS，需要卸载重新安装
{: .prompt-tip }

步骤流程如下：

1. 安装对应的 VS，确保安装了如下组件
  
   - .NET desktop development
   - Desktop development with C++
   - Universal Windows Platform development
   - Game development with C++ 
2. 右键 `xxx.uproject`，选择 `Generate Visual Studio project file`
3. 重新双击打开 UE 项目

