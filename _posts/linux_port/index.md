---
title: Linux端口号被占用
date: 2023-01-13
tags:
  - Linux
keywords:
  - 端口port
---

先查询占用端口号进程

```
netstat -apn | grep 8080
```

![](1.png)

删除进程

```
kill -9 pid
```

再回看8080是否还有进程

```
netstat -apn | grep 8080
```

