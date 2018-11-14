---
title: '使用Docker 安裝 Grafana'
date: 2018-10-19 11:50:40
categories: 筆記
tags: 
- Grafana
- Docker
---

# Grafana Docker 指令

### Grafana
https://hub.docker.com/r/grafana/grafana/

```
docker run -d -p 3000:3000 --link InfluxDb:influxdb --restart=always --name 
grafana grafana/grafana:4.6.2
```
### InfluxDb
https://hub.docker.com/_/influxdb/

```
docker run -d -p 8083:8083 -p 8086:8086 -e INFLUXDB_ADMIN_ENABLED=true --name InfluxDb --restart=always influxdb:1.1
```
###  telegraf
https://github.com/influxdata/telegraf
