---
title: Docker Nginx Reverse Proxy
date: 2018-12-10 14:55:44
categories:
- 學習
tags:
- Docker
- Nginx
---

## Docker Nginx Reverse Proxy

### 建立 nginx.conf

#### 建立 nginx_reverseproxy 資料夾 
```
mkdir nginx_reverseproxy
cd ngixn_reverseproxy/
```
#### 建立 nginx.conf
```
touch nginx.conf
```
#### 編輯 nginx.conf 
```
vi nginx.conf 
```
> 輸入 i可以進入編輯模式
> 輸入 ESC離開編輯模式，在輸入 ":wq"存檔
> 刪除資料夾可以使用 "rm -r 資料夾名稱"

#### 設定 nginx.conf 
```
events {
 
}

http {
server {
  listen 80; 
  server_name www.google.com;
  location / {
    proxy_pass http://www.google.com;
  }
}
}
```

## Run Docker Nginx

```
docker run --name proxy_nginx -v /nginx_reverseproxy/nginx.conf:/etc/nginx/nginx.conf:ro -p 8088:80 -d nginx
```
### 瀏覽 Yourhost:8088
![](https://i.imgur.com/imLE42t.png)

# 參考

[[ DevOps ] Nginx 設定 Proxy Server 及 Load balance](https://oranwind.org/-devops-ubuntu-shang-nginx-an-zhuang-yu-she-ding/)
[NGINX Reverse Proxy](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)