---
title: 'Git入门-init, add和commit -v介绍'
date: 2019-01-10 13:58:10
tags:
---

Git是一个开源的分布式版本控制系统。本门主要介绍入门的git init, git add, git commit -v命令。

# git init用于**创建Git仓库**
在配置好Git后，无论是在本地使用Git，还是把本地的Git上传到GitHub，本地都需要先有Git仓库。
输入命令行：
> git init
即可在当前目录中创建一个.git目录，.git目录是用于存放所有该项目数据的。

# git add用于把文件或改动**放到缓存**
若已在仓库中新建了一个名为*new*的.txt文件，现需把*new.txt*方到缓存区。
输入命令行：
> git add *new.txt* (要放入缓存的文件名)

