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
![图片来源网络](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1547115114265&di=9de95c89898f651aca048cf82f0b45df&imgtype=0&src=http%3A%2F%2Fimage.mamicode.com%2Finfo%2F201901%2F20190109102740798912.png "git init screenshot")

# git add用于把文件或改动**放到缓存**
若已在仓库中新建了一个名为*new*的.txt文件，现需把*new.txt*方到缓存区。
输入命令行：
> git add *new.txt* (要放入缓存的文件名)


![图片来源网络](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1547115277994&di=6c6dd9ac71a1a16980cba2e9095a97d2&imgtype=0&src=http%3A%2F%2Fupload-images.jianshu.io%2Fupload_images%2F10550855-42c925e15b01d783.png "git add screenshot")

# git commit -v用于在提交前审阅改动
在命令行里输入：
> git commit -v


会进入一编辑器，在确定提交的内容无误后，填写注释就可以。
![图片来源网络](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1547115577319&di=cc695efed63cd9598211c42f69a923a3&imgtype=0&src=http%3A%2F%2Fupload-images.jianshu.io%2Fupload_images%2F15398122-f1725c383f9e5d71.png "git commit -v screenshot")