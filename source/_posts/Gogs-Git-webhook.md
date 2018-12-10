---
title: Gogs Git webhook
date: 2018-11-28 13:46:39
categories:
- 筆記
tags:
- Gogs
- webhook
- Git
- Jenkins
---

# Git Commit 後通知Jenkins 建置


### 點選倉庫設定 
![](https://i.imgur.com/6bT5cqK.png)

### 管理 Web 鉤子
![](https://i.imgur.com/BnxMzq9.png)

### 添加鉤子
![](https://i.imgur.com/HcebZ16.png)

### 選 Gogs
![](https://i.imgur.com/eZUBZL0.png)

### 推送地址 & 密鑰本文(自行定義)
![](https://i.imgur.com/HOVOc4Z.png)

```
http://Jenkins位置/gogs-webhook/?job=專案名稱
```

### Jenkins 記得安裝  Gogs Webhook Plugin 

![](https://i.imgur.com/YFMyGCe.png)

### 專案記得設定剛才的密鑰本文

![](https://i.imgur.com/Y5UFomw.png)
