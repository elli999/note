---
title: Visual Studio Code笔记
tags:
  - code
  - 编辑器
  - software
categories:
	- [+IT, Software]
date: 2020-08-18 21:17:53
---

Visual Studio Code的一些使用技巧。


<!-- vim-markdown-toc Redcarpet -->

* [Snippits](#snippits)

<!-- vim-markdown-toc -->

<!-- more -->

---

## Snippits

Snippits即“片段”的意思，在这里指可以帮我们实现快速录入的功能，例如输入`pln`，软件就会询问我们是否替换为`println`。

* 配置方法

在软件中按`Ctrl/Command`+`Shift`+`P`，按下图输入`>snippets`，鼠标点选“首选项：配置用户代码片段”。

![snippets_command](snippets_command.png)

因为VS Code可以作为多种程序开发语言的编辑器，所以对应在配置snippets的时候，也可以选择对应的编程语言进行配置。配置完成后VS Code会自动根据你正在编辑的语言，使用对应的snippets。

![snippets_choose](snippets_choose.png)

这里我们以go语言为例，在下图输入/选择`go (Go)`。

![snippets_choose_go](snippets_choose_go.png)

现在，成功打开Go语言的snippets配置文件

![snippets_go_edit](snippets_go_edit.png)

编辑方法模板：

```
"自定义一个名字":{
    "prefix": "这里填用户需要输入的内容",
    "body": "这里是替换的内容",
    "description": "对这个功能描述的提示信息"
}
```

其中`$0`表示替换后光标停留的位置。

下面举例说明。例：实现输入`pln`时，软件提供`fmt.Println()`文本给我们选择替换。输入`pf`时，软件提供`fmt.Printf("")`文本。

```
{
	"println":{
		"prefix": "pln",
		"body":"fmt.Println($0)",
		"description": "输出行"
	},
	"printf":{
		"prefix": "pf",
		"body": "fmt.Printf(\"$0\")",
		"description": "printf输出"
	}
}
```

编写完成后保存并关闭文件即可生效。

以后我们每次需要输出行时，只需要输入文本`pln`，VS Code便会弹出当前的`pln`代码可替换的提示，在弹出框体后，再次按Enter或者Tab即可完成替换。
