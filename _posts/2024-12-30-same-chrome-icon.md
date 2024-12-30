---
title: '默认打开方式中出现两个相同的 Google Chrome'
date: 2024-12-30 16:12:20 +0800
categories: [bug]
tags: [windows]
---

## 问题描述

默认打开方式(Default apps)中出现两个一样的 Google Chrome ，其中一个显示损失，另一个可正常使用

## 解决方法

1. 先将安装的 Google Chrome 删除
2. 打开注册表编辑(Registry Editor)，搜索 `Computer\HKEY_LOCAL_MACHINE\chrome`, 将带 `Chrome` 前缀的项全部删除
3. 重新安装 Google Chrome

> 注意事项：在删除前最好先保存一份，防止误删
{: .prompt-warning}
