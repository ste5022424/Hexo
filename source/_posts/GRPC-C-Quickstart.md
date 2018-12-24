---
title: 'GRPC C# Quickstart'
date: 2018-12-11 14:15:11
categories:
- 筆記
tags:
- GRPC
---

## GRPC Quickstart

### Clone GRPC
```
git clone -b v1.17.0 https://github.com/grpc/grpc 
```
![](https://i.imgur.com/F5MAgGK.png)

### Build 
```
cd D:\GRPC\grpc\examples\csharp\Helloworld
dotnet build Greeter.sln
```
![](https://i.imgur.com/p9eDKj6.png)

### Run a gRPC application

> Server
```
cd D:\GRPC\grpc\examples\csharp\Helloworld\GreeterServer>
 dotnet run -f netcoreapp2.1
```
![](https://i.imgur.com/snarP0h.png)


> Client
```
cd D:\GRPC\grpc\examples\csharp\Helloworld\GreeterClient
dotnet run -f netcoreapp2.1
```

![](https://i.imgur.com/xQDQpZC.png)

## 參考
[C# Quickstart](https://grpc.io/docs/quickstart/csharp.html)
[gRPC 官方文檔中文版 V1.0](https://doc.oschina.net/grpc?t=60132)
[https://github.com/grpc/grpc](https://github.com/grpc/grpc)