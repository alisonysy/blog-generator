---
title: Git入门-简单操作命令介绍
date: 2019-01-10 15:45:49
tags:
---

Git的操作命令繁多，以下是常用的几个：

1. ls
ls用于列出当前目录下的文件，使用方法：
> ls

但只用ls并不会显示以 .开头的隐藏文件，若要显示隐藏文件，则需使用：
> ls -a

2. cat
cat可用于列出文档内容，把A文档内容移至/添加到B文档中。
**列出文档内容**
> cat *file name*

**把A文档内容移至到B文档中**
此时B文档的内容将被A文档的内容替换掉。
> cat *A* > *B*

**把A文档的内容添加到B文档中**
此时B文档的内容**不会**被A文档的内容替换掉。
> cat *A* >> *B*

3. mv
mv用于重命名或移动该文件：
> mv *file name* *新的文件名/移动的目标路径*

4. touch
touch用于创建新文件：
> touch *file name*

### 如何用ExplainShell搜寻命令使用方法
当遇到某个命令不明白其使用方法时，可登陆[ExplainShell](https://explainshell.com/)并输入该命令，即可查看该命令的作用。