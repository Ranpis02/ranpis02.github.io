---
title: '使用 Vagrant 管理 VMware 上的虚拟机'
date: 2024-11-18 23:44:11 +0800
categories: [vagrant]
tags: [vmware, vagrant]
---

## 安装 VMware 虚拟机

由于 VMware 目前允许可以个人使用，因此我们可以直接下载安装，如果直接到官网上安装，可能需要填写表单注册，比较麻烦，所以这里推荐直接到镜像站下载即可，推荐下面两个

1. <https://www.techspot.com/downloads/189-vmware-workstation-for-windows.html>
2. <https://softwareupdate.vmware.com/cds/vmw-desktop/ws/>

> 链接 1 直接下载后即可安装使用，但是需要挂代理，并且该链接只提供 vmware workstation(windows), 不提供 vmware fusion(mac)；链接 2 找到对应版本号和平台后下载进入 `core` 文件夹进行下载
{: .prompt-tip}

🔑 技巧：如果想要将下载的 VMware 从中文语言修改为英文，只需要找到安装目录下的 `messages` 文件夹，然后将 `zh_CN` 语言包删除或者修改名称即可

## 安装 Vagrant

对于 Windows 平台，推荐使用包管理工具 `scoop`(或者 `winget`)，安装的命令如下：

```shell
scoop install vagrant
```

安装完成后，配置 `.vagrant.d` 的位置，通过 `vagrant` 下载的 box 都会存放在该目录下，具体操作如下，在 `查看高级系统设置` 中添加环境变量，之后在系统变量或者用户变量中添加一个 `VAGRANT_HOME: vagrant_d_path` 的键值对即可

### 1. 安装插件

1. 下载 [Vagrant VMware Utility Installation](https://developer.hashicorp.com/vagrant/docs/providers/vmware/vagrant-vmware-utility)
2. 下载vmware-desktop插件:

   ```shell
   vagrant plugin install vagrant-vmware-desktop
   ```

### 2. 下载镜像并进行初始化

> 查看镜像仓库：<https://portal.cloud.hashicorp.com/vagrant/discover>
{: .prompt-tip}

以 `centos/7` 为例：

1. 找到一个目录进行初始化

   ```shell
   vagrant init centos/7 --box-version 2004.01
   ```

2. 开始远程安装并启动

   ```shell
   vagrant up
   ```

安装完成后打开 VMware 发现列表中没有 `centos/7`，找到 VMware 底部托盘，选择 `打开全部后台虚拟机` 后即可看到。
