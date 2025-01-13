---
title: 'Scoop 的基本使用'
date: 2024-12-02 19:03:11 +0800
categories: [tools]
tags: [scoop]
---

## 配置安装路径

`Scoop`是 Windows 的包管理器，相较于 `Chocolately` 和 `Winget`, 其可以自定义安装位置，而不需要像前两者一样必须安装到 C 盘，但也正是由于它的这个特点，使得对安装的程序要求比较严格，像 IDM 或 docker-desktop 这类必须安装到 C 盘或者需要管理员权限的程序就未被收录到其 `bucket` 中。

- Scoop 默认安装软件的路径为 `C:\Users\<USERNAME>\scoop`
- Scoop 默认安装的全局路径为 `C:\ProgramData\scoop`

自定义安装方法

- 手动添加：在 `用户变量` 和 `全局变量` 中分别添加相对应的路径
- 命令行添加

  ```shell
  # 添加用户变量
  $env:SCOOP='D:\Scoop'
  [Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')

  # 添加系统变量
  $env:SCOOP_GLOBAL='D:\Scoop\Global'
  [Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
  ```

## 开始安装

- 对于非管理员账户而言，安装命令如下：

  ```shell
  # 改变 powershell 的执行策略，允许执行本地脚本
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

  # 安装命令
  Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
  ```

  > 参考：<https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.4>
  {: .prompt-tip}

### 安装必要程序

```shell
# 类似于 Linux, 得到 root 权限的命令
scoop install sudo 

# 拉取 git 仓库(这里更加推荐无 GUI 界面的 mingit，而不是 git)
scoop install mingit

# 解压软件
scoop install 7zip

# 安装多线程下载工具
scoop install aria2

# 安装指令工具（附）
scoop install curl grep sed less touch
```

## 使用指南

`bucket` 是 app 的集合，Scoop 默认为我们提供 `main` 这个 `bucket`, 但是更多的 app 安装到 `extras` 中，因此我们需要添加一个 `extras`

### 查看，添加和删除 bucket

```shell
# 查看当前已添加 bucket 列表
scoop bucket list

# 查看可用 bucket 列表
scoop bucket known

# 添加 bucket 
scoop bucket add <bucket_name> 

# 删除 bucket
scoop bucket rm <bucket_name>
```

### 查找，安装，更新和删除 app

```shell
# 查找 app
scoop search <app_name>

# 仅下载 app 
scoop download <app_name>

# 安装 app
scoop install <app_name>

# 更新 app
scoop update <app_name>

# 更新全部 app
scoop update *

# 删除 app
scoop uninstall <app_name>

# 查看 app 主页
scoop home <app_name>
```

### 进阶命令

```shell
# 将程序为所有用户安装 
scoop install <app_name> -g

# 更新 scoop 以及 bucket
scoop update

# 禁止更新 app
scoop hold <app_name>

# 清除 app 以及配置文件
scoop uninstall <app_name> -p

# 清除软件旧版本
scoop cleanup *

# 清除软件缓存（即 cache 文件夹中的文件）
scoop cache rm *

# 查看相关配置
scoop list

# 配置相关项
scoop config <key> <value>

# 去除配置项
scoop config rm <key>
```

## 其他更多

- scoop 库：<https://scoop.sh/>
- 中国镜像配置：<https://gitee.com/scoop-installer/scoop>
