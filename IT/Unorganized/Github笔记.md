---
title: Github笔记
date: 2020-07-31 21:54:44
tags:
    - Github
categories:
	- [+IT, Software, Github]
---

> Github的个人笔记

<!-- more -->

# Others

## 网络问题

### raw.githubusercontent.com 无法访问

> 应该是DNS的问题

* 查询真实 IP
通过 [IPAddress.com](https://www.ipaddress.com/) 查询 http://raw.githubusercontent.com/ 的真实 IP，

![Image](IPcheck.png)

可查出 `githubusercontet.com`对应的IP地址是`192.232.68.133`。

* 修改hosts

hosts文件中加入`192.232.68.133 githubusercontent.com`即可。



---
