---
title: Screen使用笔记
date: 2018-08-04 19:07:22
author: SongJF
categories: Linux技巧
tags: 
    - 工具
    - 小技巧
---

## 新建session

—>screen -S <Session名称>

## 展示所有session

—>screen -ls

## 重连session

—>screen -r <Session名称>(或ID)

## 从session中断连

—>C-a d  (C-a即ctrl+a)

## 释放某个session（杀死）

—>ctrl+d（在此session中）

—>screen -X -S test quit（在主session中）