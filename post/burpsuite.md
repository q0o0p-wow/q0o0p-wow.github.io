---
title: burpsuite的使用
date: 2019-11-12 20:32:48
tags:
---

## 1.配置

### Firefox
![](1.png)

---
扩展：
http请求方式：
HTTP1.0定义了三种方法：GET ,OPST, HEAD
HTTP1.1新增加了五种： OPTIONS ,PUT, DELETE.TRACE,CONNECT

GET 请求指定的页面信息，并返回实体主体。
HEAD 类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头
POST 向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。
PUT 从客户端向服务器传送的数据取代指定的文档的内容。
DELETE 请求服务器删除指定的页面。
CONNECT HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。
OPTIONS 允许客户端查看服务器的性能。
TRACE 回显服务器收到的请求，主要用于测试或诊断。

