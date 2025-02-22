---
title: 'Git 使用问题集合(持续更新中)'
date: 2025-02-23 00:33:18 +0800
categories: [tools]
tags: [git]
---

## 1. There is no tracking information for the current branch.

### 问题描述
```shell
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=remote/<branch> main
```

### 解决方法

出现这种问题，主要是由于本地分支没有和远程分支建立其联系，因此我们只需要按照输出的 log 提示进行处理即可
1. 指定需要拉取的分支。`<remote>` 为 remote name，`<branch>`为 branch name
   ```shell
   git pull <remote> <branch>
   ```
2. 跟踪分支。`<local_branch>` 为 local branch name
   ```shell
   git branch --set-upstream-to=<remote>/<branch> <local_branch>
   ```

