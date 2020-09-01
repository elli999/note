---
title: Go笔记
tags:
  - Go
  - coding
categories:
	- [+IT, Coding, Go]
date: 2020-08-17 22:41:05
---

My Go wiki.


<!-- vim-markdown-toc Redcarpet -->

+ [Go命令](#go命令)
	* [go build](#go-build)
	* [go install](#go-install)
+ [编译](#编译)

<!-- vim-markdown-toc -->

<!-- more -->

---

# Go命令

## go build

把当前路径下的go文件编译成可执行的程序。

* go build -o 文件名


* 跨平台编译

`go build`默认得到的是当前操作系统的可执行文件，下面介绍在一个系统下编译另一个系统的可执行文件。

以**编译Linux平台64位程序**为例：

在terminal下指定目标操作系统的平台和处理器架构

```Go
SET CGO_ENABLED=0  // 禁用CGO
SET GOOS=linux  // 目标平台是linux
SET GOARCH=amd64  // 目标处理器架构是amd64
```

> 使用了cgo的代码是不支持跨平台编译的

设置好后正常使用`go build`进行编译即可得到Linux下的可执行文件。

对其他系统进行编译的操作方法也是一样，只需要把`SET GOOS=系统名`进行对应更换即可，其中windows平台就是填写`windows`，linux平台就是`linux`，而Mac是`darwin`，其它不变。


## go install

`go install`就是把编译完成后得到的可执行文件放置到`GOPATH`的`bin`目录下。因为环境变量中配置了该目录，所以可以在任何路径运行可执行文件。

<br>

--------

# 编译

使用terminal进入项目文件夹内，运行`go build`命令进行编译。


