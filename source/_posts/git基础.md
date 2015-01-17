title: git基础
date: 2015-01-17 14:50:16
tags: [git, code]
---

### 简介

git是linus大神在linux kernel后的又一个牛逼的项目

git很强大，功能很多，如果有兴趣研究，推荐<git权威指南>，很厚的一本书，里面有 git 的各种操作，以及在本地搭建 git 服务器和用 gerrit 做 review 等等
 
很多人在搜索git与svn的时候，会在网上看到说git是分布式的。嗯，这个是对的，但是大多数情况下我们还是一个remote repo多个local repo这种比较常见。
remote repo在我们这边指的就是 github 上托管的某个项目。
 
一个git repo中包括有几种类型的文件。1）untracked。2）tracked but not modified。3）tracked, modified, staged。 4）tracked, modified but not staged。5）在 .gitignore中被ignore的文件
首先用 git clone <repository>  <directory>；
 
repository指的是项目的地址，可以是git协议，或者https，协议，也可以是文件协议等等。执行完后会在当前目录生成一个目录，directory是选填的，如果不填，则目录名即repository的名字，否则为         directory的名字
 
### 常用的命令有
* git status： 查看当前repo中的所有文件状态（看不到被 5）被ignore的文件）
* git log: 查看提交的历史
* git add :  可以把未被跟踪的文件加入跟踪，或者把已被跟踪且修改的文件变为待提交的。1)–>3);   4)-->3)
* git checkout COMMIT – PATH： 将COMMIT这次COMMIT中的某个文件检到本地工作区，一般经常用来还原某个修改过但想去掉修改的文件
* git commit：把待提交的文件提交到本地repo
* git reset: 还原到某次提交，可以只还原提交，也可以同时还原提交和改动的文件，有三个较常用的可选参数 --soft, --mixed, --hard，默认是–mixed
* git pull：通过远程的repo来更新本地的repo
* git push: 将本地的repo更新到远程的repo
* 上述几个命令基本可以满足单个branch的开发需要

### 多个branch操作：
* git branch: 查看本的所有branch，加上 -a 可以查看到远程的branch
* git merge a b: 把branch a的合并到branch b，可能出现冲突。但是branch a不发生变化
* git rebase x: 去掉当前branch与branch x的分歧，可能出现冲突。功能与merge相似，一般用在某个feature的分支中对master做rebase
* git checkout y: 切换到branch y
* git checkout -b z: 根据当前分支生成新branch z，并直接切换到branch z
 
### 版本控制相关操作：
* git tag: 有多个参数来做
* git tag -a tagname COMMIT: 生成annoated的tag, COMMIT选填，如果不填，则为当前的commit
* git tag -d tagname: 删除tagname这个tag
* git checkout tagname: 切换到tagname这个tag所在的commit
* git push --tags: 将本的的所有tag推送到远程repo
 
### 本地自建repo：
* git init: 初始化一个repo，可以加--bare来生成一个只记录信息没有文件的repo
 
> 本人能力有限，表达不太清楚，如果有问题可以互相交流学习(jayzh1010@gmail.com || jieliang.zhang@ele.me)
网上也有很多的git教程，写的也都比较详细
其实最有用的文档都在电脑上，善用man和–help
如:
git checkout --hlep
git tag --help
git init --help
