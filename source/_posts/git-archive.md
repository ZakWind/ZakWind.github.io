---
title: git 增量打包
date: 2021-06-27 00:28:11
tags: git
description: 数据类项目一般投产上线都是以脚本和表为单位，只需要打包有修改的脚本，所以需要增量打包
---

## 前置基础知识点

### git diff

`git diff --name-only` 可以输出两个版本之间内容不同的文件名，具体参考 [git diff](https://git-scm.com/docs/git-diff)

e.g.

``` shell
$ git diff 24aa42a d0d7112 --name-only
```

### git archive

git 的打包命令，可以批量打包选定分支和版本的文件，具体参考 [git archive](https://git-scm.com/docs/git-archive)

e.g.

``` shell
$ git archive -o dist.zip HEAD
```



## 增量打包方案

``` shell
git archive -o update.zip master $(git diff 24aa42a d0d7112 --name-only)
```

适用于 bash、shell 等，不支持 windows cmd，不支持删文件。

分支合并、变基等操作都是不影响的，因为本质上是比较两个版本文件的区别。所以有变化的文件都会被打包。

建议 windows 适用 python 编写脚本进行打包，使用 `git diff` 获取文件名后，将文件复制到打包目录。
