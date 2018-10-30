title: git
author: wangHianHui
date: 2018-11-28
tags:  
- git
categories: ['git']
---
1、npm与yarn常用命令对比
<!-- more -->
 ![yarn-npm](/img/yarn-npm.jpg "yarn-npm")

2、git 撤销
> git reflog (可以查看所有分支的所有操作记录（包括commit和reset的操作），包括已经被删除的commit记录，git log则不能察看已经删除了的commit记录)
git reset --hard (commit id) 回退到某版本
git push origin (branch) 提交到远端