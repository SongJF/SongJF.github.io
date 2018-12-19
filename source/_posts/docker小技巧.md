---
title: docker小技巧
author: SongJF
date: 2018-12-19 19:23:27
categories:  后端
tags:
    - docker
    - 小技巧
---
<!-- TOC -->

- [docker-compose使用本地yml文件启动容器](#docker-compose使用本地yml文件启动容器)
- [构造`docker-compose`配置文件](#构造`docker-compose`配置文件)

<!-- /TOC -->
## docker-compose使用本地yml文件启动容器

<!--more-->

指定yml并后台部署

```
docker-compose  -f ./XXXX.yml  up -d
```

## 构造`docker-compose`配置文件

`docker-compose.yml`模板

```
version: '3'
services:
  redis:
    container_name: test-redis
    image: redis
    environment:
      - redis-server
      - appendonly=yes
    volumes:
      - ./redis/redis.redis.conf:/etc/redis/redis.conf/
      - ./redis/data:/data
    ports:
      - "6379:6379"

```
