---
title: Docker compose Run Redis
date: 2018-12-12 16:32:46
categories:
- 筆記
tags:
- Docker
- Redis
- Docker compose
- Visual Studio Code
---

## Docker compose Run Redis

### 建立資料夾 及 Dockerfile 

```
 mkdir composeredis
 cd composeredis
 vi docker-compose.yml
```
### Dockerfile

```
version: "3"
services:
  redis:0000000.
    image: redis
    ports: 
     - "1233:6379"
    volumes: 
     - "./tmp/redis:/data"

```
### docker-compse run redis
```
docker-compose up -d
```
![](https://i.imgur.com/fzhLCey.png)

### docekr ps -a
![](https://i.imgur.com/oCA5fVw.png)

### 連線測試

```
telnet 127.0.0.1 1233
set mykey 999
get mykey 
```
![](https://i.imgur.com/zz3UsVZ.png)