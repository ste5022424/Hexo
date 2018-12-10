---
title: Python redis
date: 2018-12-06 10:20:32
categories:
- 筆記
tags:
- python
- redis
---

# Python redis

```
import redis
r = redis.Redis(host='localhost', port=6379, db=0)
r.set('foo', 'bar123123132')
print(r.get('foo'))

```

![](https://i.imgur.com/pOuqySo.png)


# 參考

[https://pypi.org/project/redis/](https://pypi.org/project/redis/)