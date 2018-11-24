---
title: git小技巧
author: SongJF
date: 2018-08-07 16:24:39
categories: git
tags: 小技巧
---


## 切换分支

- git remote add origin [url] 添加新的远程仓库

- git push origin [branch] 本地推到远程分支

<!-- more-->

## 删除分支

- git branch -d [branch] 删除本地分支

- git remote rm origin 删除远程分支

# 分支合并

- git merge master feacher 合并分支(b到a)

- git rebase a b         b到a变基

## 冲突处理

- 使用vsode 据提示处理....

## 存储

解决工作未完成时需与远程仓库同步时的情景

- git stash (save [name]) 将暂存存入存储

- git stash apply 弹出存储的内容