---
title: '重装电脑札记'
date: 2025-01-27 21:23:33 +0800
categories: [tools]
tags: [windows]
---

## 制作启动盘(Bootable USB Drives)

> 在重新装机之前，必须要确保原来电脑的重要数据已经转移
{: .prompt-warning }

准备工具
- [Rufus](https://rufus.ie/en/): 用于制作启动盘的软件
- 8GB 以上的 U 盘
> 如果你的 U 盘不支持大文件写入，大概率是由于 U 盘的 FS 格式为 FAT32 等，该格式无法存入 4GB 大小以上的单文件，解决方法就是将其文件系统格式化为 NTFS
{: .prompt-tip }

从 Windows 官网中下载好 [Windows11](https://www.microsoft.com/en-us/software-download/windows11) 或者 [Windows10](https://www.microsoft.com/en-us/software-download/windows10) 对应的镜像，**将其放到电脑本地磁盘中**，然后选好启动的镜像
> 在为 U 盘制作启动盘时，U 盘内原来的所有文件都会被删除，所以不要将 `.iso` 文件放在 U 盘
{: .prompt-warning }

基本设置如下，`image option` 如果设置为 `Windows To Go` 代表将系统直接安装到 U 盘中，`File system` 如果设置为 `ReFS`，则存在严重的不兼容问题，所以设置保持默认即可，没有特殊情况不要进行更改 

<img src="https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/image-20250128002110971.png" alt="image-20250128002110971" style="zoom: 67%;" />

对于体验设置，移除 `TPM2.0` 模块是必选的，其他可以根据自己情况。如果自己有微软账户，需要和微软账户保持同步，建议不移除微软账户(online microsoft account)，反之移除并且创建一个本地账户(local account)。同时，建议将 `BitLocker` 也移除（最新版有对应选项），`BitLocker` 加密容易导致数据丢失以及影响读写速度，总体而言弊大于利。

<img src="https://thinkbook16-blog-img.oss-cn-zhangjiakou.aliyuncs.com/img_for_typora/image-20250128124342035.png" alt="image-20250128124342035" style="zoom: 80%;" />

## 开始重装

U 盘启动：重启电脑，进入 `BIOS` 界面，以 U 盘启动，例如对于 lenovo 而言，重启后看到欢迎界面，按 `F12` 进入启动选择界面，然后选择带有 `USB` 的启动方式
> 启动时，如果出现 "EFI USB device has been blocked by the current security policy" 提示，那么进入 `BIOS` 将 `secure Boot` 中 `security` 选择 `disable` 即可，对于 lenovo ，按键为 `F1`
{: .prompt-tip }

## 注意事项

1. 如果发现自己电脑没有连接宽带，无法连接网络下载网卡驱动，可以使用 USB 连接电脑和手机，然后打开手机的 `USB tethering`(USB 网络共享)
2. 安装系统到磁盘时，先删除之前的磁盘分区删除，然后合并到一个盘，重装完成后，如果有分盘需求再到 `Disk Management` 中进行分盘

