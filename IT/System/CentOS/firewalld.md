
<!-- Docsify/note/IT/System/CentOS/firewalld.md -->


<!-- vim-markdown-toc Redcarpet -->

* [查看firewall服务的状态](#查看firewall服务的状态)
* [查看firewall的状态](#查看firewall的状态)
* [Command](#command)
    - [start](#start)
    - [restart](#restart)
    - [stop](#stop)
    - [查看防火墙规则](#查看防火墙规则)
    - [查询端口是否开放](#查询端口是否开放)
    - [开放端口](#开放端口)
    - [关闭端口](#关闭端口)
    - [重启防火墙(修改配置后要重启防火墙)](#重启防火墙-修改配置后要重启防火墙)

<!-- vim-markdown-toc -->

<font size=10>本文内容是CentOS 7的命令，如果是6的话命令有所不同，请注意！！</font>

> firwall-cmd：是Linux提供的操作firewall的一个工具；

## 查看firewall服务的状态

```
# 查看状态
systemctl status firewalld

# 开启
systemctl start firewalld
 
 # 设置开机自启
 systemctl enable firewalld
 
# 关闭
systemctl stop firewalld
 
# 禁止开机自启
sytemctl disable firewalld
```

主要是看“Active“那一行，如果是“inactive(dead)“则是未启动，如果是“active (running)“则是正在运行。

## 查看firewall的状态

```
firewall-cmd --state
```

```
# 重启firewall
firewall-cmd --reload
```

## Command


### start

开启firewalld.service服务

```
service firewalld start
```

### restart

重启firewalld.service服务

```
service firewalld restart
```

### stop

停止firewalld.service服务

```
service firewalld stop
```

### 查看防火墙规则

```
firewall-cmd --list-all 
```

### 查询端口是否开放

```
firewall-cmd --query-port=8080/tcp
```

### 开放端口

```
firewall-cmd --permanent --add-port=8080/tcp
```

### 关闭端口

```
firewall-cmd --permanent --remove-port=8080/tcp
```


### 重启防火墙(修改配置后要重启防火墙)

```
firewall-cmd --reload
```

