---
title: Git 常用命令总结
date: 2019-07-12 11:03:57
tags:
  - git
categories:
  - 工具
---

### 仓库初始化

```bash
git init #创建一个空的Git仓库
```

### 查看远程仓库信息

```bash
git remote #查看远程仓库 显示origin

git remote -v #查看远程仓库 并显示地址

git remote add [name] [url] # 为仓库添加远程地址

git remote rm origin #删除仓库的远程地址
```

### 查看状态

```bash
git status
# 命令用于显示工作目录和暂存区的状态。使用此命令能看到那些修改被暂存到了, 哪些没有
```

### 添加索引

```bash
git add <path>
#此命令将要提交的文件的信息添加到索引库中(将修改添加到暂存区)

$ git add .  # 将所有修改添加到暂存区
```

### 提交

```bash
git commit
#命令将索引的当前内容与描述更改的用户和日志消息一起存储在新的提交中

$ git commit -m 'first commit'
```

### 推送

```bash
git push -u origin master #将本地的master分支推送到origin主机的 master分支

#如果 master不存在，则会被新建;-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push
```

### 操作分支

```bash
git branch #命令用于列出，创建或删除分支

$ git branch # 查看本地分支
$ git branch -r # 查看远程分支
$ git branch -a # 查看本地和远程分支
$ git branch -d # 删除本地分支
$ git push origin --delete # 删除远程分支


$ git branch dev1.0 # 新建 dev1.0 分支

$ git checkout dev1.0 #切换到 dev1.0 分支上
$ git branch -m dev1.0 dev1.1 #修改 dev1.0 名称改为 dev1.1

$ git checkout dev1.0 #先切换到 dev1.1 分支上
$ git branch -d dev1.0 # 再删除 dev1.0 分支

```

```bash
git merge # 分支合并

$ git checkout dev1.0 # 切换到 dev1.0 分支上
$ git merge dev1.1 # 将 dev1.1 分支 合并到 当前分支 (dev1.0)
```

### 拉取

```bash
git pull <远程主机名> <远程分支名>:<本地分支名>

git pull # 取回远程主机某个分支的更新，再与本地的指定分支合并

$ git pull origin dev1.1
```
