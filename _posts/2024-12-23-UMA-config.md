---
title: 'UMA 相关知识'
date: 2024-12-23 14:30:33 +0800
categories: [hardware]
tags: [uma, hardware, gpu]
---

## UMA 介绍

UMA: 全称为 "Unified Memory Architecture"，即是内存统一架构，是指没有独显的机器，在主板上集成了显卡，需要使用内存来作为显存，以下列示例电脑为例。

PC 信息:

- PC name: ThinkBook 16 G6+
- RAM: Samgung LPDDR5 8GB × 4
- SSD: Union Memory 1 TB
- Processor: AMD Ryzen 7 8845H w/ Radeon 780M Graphics

在了解示例电脑的基本信息后，我们打开 `Task Manager`, 切换到 `GPU` 一栏，我们可以看到自己 `Dedicated GPU` 和 `Shared GPU` 具体大小，如下：
![image-20241223145956819](https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/image-20241223145956819.png)

## 调整 UMA

UMA 的大小会影响可用内存大小，如下
![image-20241223151244054](https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/image-20241223151244054.png)

在这台电脑中，`UMA Frame Buffer Size` 可选的调整大小有：1GB、2GB、4GB，调整策略如下：

- 日常办公：1GB
- 图像处理或轻量游戏：2GB
- 视频编辑、3D建模或大型游戏：4GB

> 通常而言，如果 RAM > 16GB，UMA 选择 4GB；如果 RAM > 8GB && RAM <=16GB，UMA 选择 2GB；否则都选择 1GB 或者更小
{: .prompt-tip}

调整方法：进入 BIOS -> 定位到 `UMA Frame Buffer Size`(lenovo 的在 display 中) -> 设置相应大小
