---
title: Docker compose Run Redis
date: 2018-12-12 16:32:46
categories:
- 筆記
tags:
- Docker
- Redis
- Visual Studio Code
---



```
version: '1'

services:

  redis:
    name:  'redis'
    image: redis
    ports: '6379:6379'
    volumes: '/data/redis:/data'

```
