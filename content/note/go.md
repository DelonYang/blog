---
title: "Go"
date: 2019-03-07T15:38:54+08:00
---
# Go

## goscript

### 1. Http
1. 获取http请求的IP，Path

    ```go
    ip, port, err := net.SplitHostPort(req.RemoteAddr)
    path := req.URL.Path
    ```
