---
title: '由于安全模式发生更改导致 PIN 不可用'
date: 2025-01-24 23:20:30 +0800
categories: [bug]
tags: [windows]
---

## 背景

心血来潮，准备下载一个雷电模拟器重温童年经典`涂鸦地带`，结果打开后显示`VT 未启用`，查找了下原因发现是由于`内核隔离(core isloation)`的问题，当我将`内核隔离`关闭并重启电脑后出现了`PIN 不可用`的提示

## 解决方案

重新后，连接热点或 Wifi，点击下面的警示框，重新设置 PIN 即可。

## 预防方案

`WIN + I`进入 windows 的设置界面，然后转到 `Accounts(账户) → Sign-in options(登录选项)`，将其他设置（Additional Settings）的 "仅允许此设备上的微软账户使用 Windows Hello 登录" 取消勾选即可防止再次出现这种情。
