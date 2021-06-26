---
title: git 瘦身
date: 2021-06-27 01:00:04
tags: git
description: 后悔把一些文件和文件夹纳入仓库管理，强迫症要清理历史时
---

版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
本文链接：https://blog.csdn.net/qq_40233736/article/details/86668768

## Quick Start

> 多人协作仓库不要进行这些操作

``` shell
# 从历史中删除 target/ 这个文件夹
git filter-branch --force --index-filter 'git rm -r  --cached --ignore-unmatch target/' --prune-empty --tag-name-filter cat -- --all
# 执行仓库压缩
git gc --prune=now
# 推送到远程仓库
git push origin --force --all
```
