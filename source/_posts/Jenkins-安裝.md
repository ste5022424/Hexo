---
title: '使用Docker 安裝 Jenkins'
date: 2018-10-19 11:50:40
categories: 筆記
tags: 
- Jenkins
- Docker
---

## 使用Docker 安裝 Jenkins

### 安裝 jenkins

```
docker run --name myjenkins -p 8080:8080 -p 50000:50000 -v /var/jenkins_home jenkins
```
     
### 取得密碼(initialAdminPassword)
```    
$ docker exec jenkins-master cat /var/jenkins_home/secrets/initialAdminPassword
```

### 進入Jenkins
http://127.0.0.1:8080/


## 參考網址
[Jenkins On Doker](https://hub.docker.com/_/jenkins/)
[Get Started with Jenkins 2.0 with Docker](https://www.cloudbees.com/blog/get-started-jenkins-20-docker)


