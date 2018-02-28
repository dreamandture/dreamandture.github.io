---
title: git 使用
date: 2018-02-28 17:54:59
categories: develop
tags:
   - develop

---
git 的安装与使用。乱七八糟的整理
<!-- more-->

##1.git安装

ubuntu：

```sh
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \
  libz-dev libssl-dev

$ apt-get install git-core

$ git --version
git version 1.8.1.2
```

centos:

```sh
$ yum install curl-devel expat-devel gettext-devel \
  openssl-devel zlib-devel

$ yum -y install git-core

$ git --version
git version 1.7.1
```

用户信息：

```sh
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```
查看配置：

```sh
git config --list
git config user.name
```
##2.基本命令
创建仓库：

```sh
git init
#or
git init <dir>

```

提交：

```sh
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'
git tag -a v0.9 85fc7e7 #追加标签
```

克隆仓库：

```sh
git clone <repo>
git clone <repo> <directory>
```

查看更改

```sh
git log --oneline
git log --oneline --decorate --graph
git diff commit-id-1 commit-id-2 
```

回滚

```sh
git reset --hard commit-id-1
```

标签

```sh
git tag -d <tagname> #删除标签
git tag -a v0.9 <commit-id> #将标签应用到某次提交
git tag -a version -m "note" 
#git tag 是打标签的命令，-a 是添加标签，其后要跟新标签号，-m 及后面的字符串是对该标签的注释。
git show <tagname>


```

###分支
```
#查看分支
git branch
git branch -v
#切换分支
git checkout [分支名称]
```


```
git pull <远程主机名> <远程分支名>:<本地分支名>

git push <远程主机名> <本地分支名>:<远程分支名>

删除远程分支
git push <远程主机名> 空:<远程分支名>
git push origin :mysite
删除本地分支
 git branch -d <本地分支名>
 git branch -d  mysite

```