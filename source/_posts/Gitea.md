---
title: Gitea
date: 2018-12-25 11:28:29
categories:
- Gitea
tags:
- Gitea
- Git
---
## Gitea

### 建立儲存庫資料夾
```
sudo mkdir -p /var/lib/gitea
```
### Docker run

```
docker run -d --name=gitea -p 10022:22 -p 10080:3000 -v /var/lib/gitea:/data gitea/gitea:latest
```

### 預覽 Yourhost:10080
![](https://i.imgur.com/OmcRKBY.png)

### 進入安裝

![](https://i.imgur.com/DznoR4g.png)

### 設定 Gitea

#### 資料庫

>可以選擇多種資料庫類型

![](https://i.imgur.com/tEwQvrd.png)

#### 一般設定 

> SSH 伺服器域名 可以設定主機的Domain
> Gitea 基本 URL 可以設定主機的Domain 或者IP
 
![](https://i.imgur.com/ZwBVomv.png)


#### 可選設定 >  管理員帳號設定

> 設定管理員帳號

![](https://i.imgur.com/ZvkuMfN.png)

###  完成之後就可以看到 git 的畫面了

![](https://i.imgur.com/2xu0ZI2.png)


## 參考

[Gitea](https://docs.gitea.io/zh-tw/)
[Gitea Docker](https://docs.gitea.io/zh-tw/install-with-docker/)