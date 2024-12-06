# Git

[TOC]

**关键词** 文档库 分支 commit节点 git索引 追踪

**Keywords** repository branch commit index/cache tracked

## 开始

```shell
cd myfolder
git init  # git 开始管理myfolder
ls -l .git
```

sdf

## 入门

```shell
git add poem.txt  # 正式加入文件
git rm 文件名
git status  # git log --graph
git diff
git commit -m "blahblah" # 存入文档库

git rm -r --cached .  # 清除缓存，使.gitignore起作用
```



## 配置

```shell
git config --global user.name "XXX"
git config --global user.email "XXX@EMAIL"
```

配置文件目录：.git/config 或 .gitconfig

## Commit 节点



```shell
git show commit Node:文件名
git tag Node名 commit Node   #自定义标签
git tag -d commit Node    # 删除标签
git reset --soft/mixed/hard commit Node # 消磁
```



## 文件操作

```shell
git grep '查找字符串' commit 节点
git blame [-L start, stop] 文件名
git mv # 重命名
git checkout 文件名 # 从文档库中取出文件
```


## 分支

分支可以和原来的项目合并或者成为独立的项目

### 基础

```shell
git branch 分支名  # 创建分支
git checkout [-b] 分支名 # 进入分支（文件夹会同步变动）
git branch -d 分支名 #删除分支
git branch -m 新分支名 #重命名分支
```

### 合并

```shell
git merge 分支
git reset --hard HEAD^  # 恢复
```


冲突：修改了文件相同的位置，修改的内容却不一样

`git pull` 解决冲突

```shell
git cherry-pick commit 节点 # 节点合并到文件夹
```

*例子*

```shell
git checkout master
git merge draft

git status
...
git merge --continue
```

### rebase 简化演进图

```shell
git checkout draft
git rebase master
```


## 远程文档库

### 拷贝、推送、拉取

```shell
git clone http://...  [本地文件夹]
...
git push origin 分支[master]

git push -u origin 分支 # 建立对应
git config -l | grep 分支 # 查询配置
```


*注* `git config --global push.default matching/simple`. push 时自动更新分支。（当远程文档有多人修改的情况）

`git pull` 更新“远程文档库”解决冲突

### 远端节点

```shell
git remote add origin[服务器代号] git@github.com:user/project.git
```


## .gitignore

```shell
# 忽略public下的所有目录及文件
/public/*
#不忽略/public/assets
!/public/assets
```

## 网络安全
### SSL

[xxx] hub push
致命错误：无法访问 'https://github.com/Freakwill/xxx.git/'：LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
[xxx] git remote set-url origin https://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@github.com/Freakwill/xxx.git


### SSH key

```shell
ssh-keygen -t rsa -b 4096 -C "xxxxxxx@xxx.com"
cat ~/.ssh/id_rsa.pub  # copy to GitHub (Settings/SSH)
eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa
ssh -T git@github.com
```

*注* SSH 主要用于远程登录和命令行操作，提供安全的远程访问和管理功能。

## hub 命令

配置 cat .config/hub
github.com:
- user: Freakwill
  oauth_token: a6b505bce913ebc277f848a0ab6deb191cb4095b
  protocol: https
