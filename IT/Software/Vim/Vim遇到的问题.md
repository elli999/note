---
title: Vim遇到的问题
tags:
  - Vim
  - bug
categories:
  - [+IT, Software, Vim]
date: 2020-08-02 19:21:37
---


# Table of Content


<!-- vim-markdown-toc Redcarpet -->

* [字符显示不全/重叠](#字符显示不全-重叠)
* [Vim内容复制不到其它程序](#vim内容复制不到其它程序)

<!-- vim-markdown-toc -->


<!-- more -->

---

## 字符显示不全/重叠

【问题】

一些中文符号（如`“”①②→`），在Vim中输入时会出现显示不全，或者和旁边的字符重叠的情况。

【解决】

[参考](http://blog.sina.com.cn/s/blog_46dac66f010006db.html)

```
set ambiwidth=double
```

--------

## Vim内容复制不到其它程序

[参考资料：知乎《如何将 Vim 剪贴板里面的东西粘贴到 Vim 之外的地方？》](https://www.zhihu.com/question/19863631)

根据平台不同，要分两种情况。先用下面命令确定你属于哪一种，

```
vim --version | grep clipboard
```

**情况一**

![+clipboard](+clipboard.png)

如果结果里你找到加号开头的+clipboard， 恭喜你，你的vim没问题

* 用 `"+y` 将选中的内容复制到系统剪贴板，效果和ctrl-c一致。
* 用 `"+p` 将剪贴板内容复制到指定位置，也可以用ctrl-v。

**情况二**

如果找到的是负号开头的`-clipboard`，说明你的vim不支持系统剪切板。需要先重新安装vim。

Linux系统

```
sudo apt install vim-gtk
```

MacOS

```
brew install vim
```

安装好之后，输入 `vim --version | grep clipboard` 命令应该已经变成`+clipboard` 了。

现在可以回到情况一进行复制了。

---
