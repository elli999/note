---
title: Go语言安装与配置
tags:
  - Go
  - coding
categories:
	- [+IT, Coding, Go]
date: 2020-08-17 20:01:08
---

Go语言的安装与配置，以及常见问题。


<!-- vim-markdown-toc Redcarpet -->

+ [下载](#下载)
+ [安装](#安装)
	* [Windows](#windows)
	* [Linux](#linux)
	* [Mac](#mac)
	* [检查安装情况](#检查安装情况)
+ [配置环境变量](#配置环境变量)
+ [Go开发编辑器](#go开发编辑器)
	* [Goland](#goland)
	* [VS Code](#vs-code)
+ [Hello World!](#hello-world)
+ [参考](#参考)

<!-- vim-markdown-toc -->

<!-- more -->

---

# 下载

国内的Go官方镜像站：https://golang.google.cn/dl/ （推荐）

Go官网下载地址：https://golang.org/dl/ （可能会出现访问不了的情况）

Windows平台和Mac平台推荐下载可执行文件版（就是带有安装过程的安装包），Linux平台下载压缩文件版。

<br>

--------

# 安装

## Windows

Go提供的安装包安装过程很简单，下载`64位的msi安装包`后，双击运行，只有安装路径可供选择，没有任何其它选项，设置好路径后便可以一直“下一步”完成安装。

## Linux

TODO

## Mac

下载可执行文件版，直接点击下一步安装即可，默认会将go安装到`/usr/local/go`目录下。 

## 检查安装情况

安装过程执行完毕后，可以打开终端窗口，输入`go version`命令，如果显示了Go的版本信息，则说明安装成功。

<br>

--------

# 配置环境变量

这里我的Go语言安装路径为`D:\Go\`，另外计划把工作路径放在`D:\WorkSpace\Go\`下。下面以这两个路径为例进行配置。

`GOROOT`和`GOPATH`都是环境变量，其中`GOROOT`是我们安装go开发包的路径，`GOPATH`是工作路径（放置代码的地方）。

> 下面内容只在windows下部署过，其它系统未试，但理论上应该是差不多的。

* 在`用户环境变量`中配置`GOPATH`，值为工作路径，我的是`D:\WorkSpace\Go\`。
* 在`用户环境变量`中的`Path`添加一行，值为工作路径下的`bin`目录，我的是`D:\WorkSpace\Go\bin`。
* 在`系统环境变量`中配置`GOROOT`为Go语言安装路径，我的是`D:\Go\`。
* 在`系统环境变量`中的`Path`添加一行，值为Go语言安装路径下的`bin`目录，我的是`D:\Go\bin`。

> 上面变量如果不存在，则自行创建；如果存在，则更改路径即可。
> Windows需要重启生效。

<br>

--------

# Go开发编辑器

Go采用的是UTF-8编码的文本文件存放源代码，理论上使用任何一款文本编辑器都可以做Go语言开发，推荐的有VS Code和Goland。VS Code是微软开源的编辑器，而Goland是jetbrains出品的付费IDE。

> 补充说明：由于VS Code对go mod模式的支持暂时还不够完善，建议大家使用Goland编辑器。

> Goland是IDE，VS Code是编辑器。

## Goland

由于是付费软件，网上有很多教程，这里就不提供了。

## VS Code

安装比较简单，去官网下载对应系统和版本即可。

下面说说插件安装

<!-- consider to delete the first pic below, if it didn't animat -->

![VSC汉化](VSC汉化.png)

![VSC界面](VSC界面.png)

现在我们要为我们的VS Code编辑器安装Go扩展插件，让它支持Go语言开发。点击上图中的“管理扩展”按钮。

![VSC插件](VSC插件.png)

点击“管理扩展”按钮后搜索“Go”，出来的第一个插件（上图）选择安装即可。

后面我们在第一次写Go代码时，VS Code会在右下角弹出提示，自动推荐很多Go插件，选择全部安装即可（Install all）。

* Windows下VSCode切换cmd.exe作为默认终端

如果你打开VS Code的终端界面出现如下图场景（注意观察红框圈中部分），那么你的VS Code此时正使用powershell作为默认终端：

![VSC_powershell](VSC_powershell.png)

建议改为`cmd.exe`作为默认的终端工具：

![VSC_cmd1](VSC_cmd1.png)

此时，VS Code正上方中间位置会弹出如下界面，参照下图挪动鼠标使光标选中后缀为cmd.exe的那一个，然后点击鼠标左键。

![VSC_cmd2](VSC_cmd2.png)

最后重启VS Code中已经打开的终端或者直接重启VS Code就可以了。

如果没有出现下拉三角，也没有关系，按下`Ctrl`+`Shift`+`P`，VS Code正上方会出现一个框，你按照下图输入shell，然后点击指定选项即可出现上面的界面了。 

![VSC_cmd3](VSC_cmd3.png)

<br>

--------
# Hello World!

为了检查安装成果，现在我们来创建第一个Go项目——`hello`。我们创建一个hello目录。

通过VS Code在该目录下新建一个名为`main.go`的文件：

```Go
package main  // 声明 main 包，表明当前是一个可执行程序

import "fmt"  // 导入内置 fmt 包

func main(){  // main函数，是程序执行的入口
	fmt.Println("Hello World!")  // 在终端打印 Hello World!
}
```

然后在VS Code的Terminal中，进入该目录（可以在VS Code中对该目录右键，打开Terminal），然后执行`go build`命令进行编译。

> 或者在其他目录执行以下命令： `go build hello` 。go编译器会去GOPATH的src目录下查找你要编译的`hello`项目。

编译得到的可执行文件会保存在执行编译命令的当前目录下，如果是windows平台会在当前目录下找到`hello.exe`可执行文件。

可在终端直接执行该`hello.exe`文件：

```Go
c:\xxxxx\hello>hello.exe
Hello World!
```

可以见到输出结果为`Hello World!`文本。至此Go安装成功！

<br>

--------

# 参考

[李文周的博客 - 《Go语言学习之路》](https://www.liwenzhou.com/posts/Go/go_menu/)

<br>

--------
