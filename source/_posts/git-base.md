---
title: git 基础
date: 2021-03-30 20:02:21
tags: git
description: 使用时查阅的基础内容
---

### 1. 配置

1. 设置个人信息

    ``` bash
    $ git config --global user.name "foo"
    $ git config --global user.email foo@bar.com
    ```

1. 查看配置

    ``` bash
    $ git config --list
    
    credential.helper=osxkeychain
    user.name=foo
    user.email=foo@bar.com
    ```

### 2. ssh

1. 新建密钥

    ``` bash
    ssh-keygen -t rsa -C 'foo@bar.com'
    ```

    公钥位置 `~/.ssh/id_rsa.pub`  
    私钥位置 `~/.ssh/id_rsa`  

### 3. 命令

1. reset

    ``` bash
    $ git reset [--soft|--mixed|--hard] [版本] [文件]
    ```

    - --mixed

        默认，可以不用带该参数。将版本库和暂存区回退到工作区

    - --soft

        将版本库回退到暂存区

    - --hard

        版本库、暂存区、工作区全部回退（慎用）
