---
title: 'SonarQubeScanner for MSBuild 使用 Jenkins Plugin'
date: 2018-11-21 10:09:37
categories:
- SonarQube
tags:
- SonarQube
- Jenkins
---

### 在 Jenkins 外掛中心 找到 SonarQube Scanner 把它安裝起來
![](https://i.imgur.com/MGOpSwT.png)

### 檢查是否安裝完成
![](https://i.imgur.com/VOpA38L.png)

### 管理 Jenkins > 設定系統 > SonarQube servers

![](https://i.imgur.com/W69D8aY.png)

![](https://i.imgur.com/djQB5ye.png)

### 啟用並且設定Sonarqube server
![](https://i.imgur.com/j0Gj3jM.png)

### Global Tool Configuration
![](https://i.imgur.com/jKyGsJC.png)

![](https://i.imgur.com/iOBJvyD.png)

### 建置步驟 > Execute SonarQube Scanner

![](https://i.imgur.com/MwY3GQ3.png)

### 設定 Analysis properties
![](https://i.imgur.com/hCnYFjN.png)

```
sonar.projectKey=TestProject
sonar.sources=. 
sonar.projectName=TestProject
sonar.projectVersion=1.0 
sonar.exclusions=**/obj/*,**/bin/*,**/packages/*
```
> sonar.exclusions 忽略掃描

### 建置專案就會開始掃描

![](https://i.imgur.com/uNnnE9D.png)

### 掃描成功
![](https://i.imgur.com/h15iB8R.png)


![](https://i.imgur.com/TTqBhsQ.png)


# 參考

[如何使用 SonarQube 檢查 PHP 專案？](https://oomusou.io/sonarqube/php/)