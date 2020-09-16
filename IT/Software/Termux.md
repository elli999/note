

<!-- vim-markdown-toc Redcarpet -->

* [Introduce](#introduce)
* [Termux](#termux)
    - [Commands](#commands)
    - [SSH](#ssh)
    - [Termux可以做的事](#termux可以做的事)
    - [Termux做不到的事](#termux做不到的事)

<!-- vim-markdown-toc -->

## Introduce

Termux is a Android app. also is a Github open source project. 不知道这种是不是属于terminal，暂时理解成是类似terminal的东西，它是一个依赖在Android系统下的命令行工具。没有Root之前是没有太多权限的。有自己的包管理工具。

包管理使用的源是境外源，Termux初始化时，及下载其它包工具时，都比较慢。可以替换为清华源（不知道国内是否还有其它Termux源）。

另外，国内有热心网友在Termux基础上开发了`Utermux`，进行了不少本地化优化，集成了一些很厉害的工具。

## Termux

### Commands


Install package:

```
pkg install [package name]
```

Remove package:

```
pkg uninstall [package name]
```

List all packages:

```
pkg list-all
```

Upgrading packages:

```
pkg upgrade
```

### SSH

一、先安装

```
pkg install openssh
```

二、手动启动 sshd

```
sshd
```

需要指出的是, sshd 监听的是8022端口而不是22号端口，因此可以使用下面命令来验证ssh服务是否开启

```
// 自己连自己测试，可不做此步
ssh localhost -p 8022
```

若要查看sshd的日志，则可以在Termux上执行

```
logcat -s 'syslog:*'
```

> 可选：添加SSH密钥
> 
> 1. 在 主动访问端 创建密钥
> 2. 在Termux（被动访问）的`~/.ssh/authorized_keys`填入该密钥
> 之后ssh访问时就不用输密码了（应该）

三、登录

在主动访问设备执行命令

```
ssh 192.168.x.x -p 8022
```

> 使用ssh登陆Termux时无需带上用户名，因为Termux是单用户系统。即使你登陆时带上了用户名，Termux也会忽略该用户名。

（可选）为了方便，我们可以配置一下ssh client的配置文件，将下面内容加入到主动访问设备的 `~/.ssh/config` 文件中。

```
Host termux
HostName 192.168.x.x
Port 8022
```

这样只需要执行 `ssh termux` 就能登陆termx了。



### Termux可以做的事

2020.09.15

目前在Termux成功做到的事：Vim+插件、nodejs的安装、docsify、SSH

### Termux做不到的事

2020.09.15

目前在Termux做不到的事：

* samba（除非在Termux里安装linux系统。在Github也有人讨论，貌似也有技术手段强行添加，不过我不想折腾，折腾出来也没法保证稳定性）

