---
title: pm2小技巧
author: SongJF
date: 2018-10-17 09:53:43
categories: 
tags: 小技巧
---

- pm2 list 列出所有进程
- pm2 monit  监视每个node进程的CPU和内存的使用情况
- pm2 restart 0 重启指定的进程
- pm2 stop all 停止所有进程
- pm2 delete 0 杀死指定的进程
- pm2 start [欲执行的命令 如yarn] [pm2参数 比如 --name --watch] [命名该进程] -- [欲执行的命令的参数]