---
title: Hexo+Markdown+Vim打造无敌笔记系统
date: 2020-06-10 23:39:45
tags: 
	- 笔记
	- note
	- VIM
	- 笔记方法学
categories:
	- [+IT, Software, Vim]
	- [+IT, Software, Hexo]
	- [笔记方法学]
---

> 本文是本人呕心沥血之作，望能对大家有所帮助！

<font size="6">**简介**</font>

使用Hexo + Vim + Markdown打造笔记系统

Hexo是一个用户量众多的静态博客框架，使用Markdown语法进行博客编写，而Vim是一个经典的编辑器，在熟练掌握三者之后进行笔记（博客）编写会如丝般顺滑，这里把Hexo博客系统来作为笔记系统使用，并将其部署在网上，我们可以随时通过任何联网设备查看笔记。（TODO：有空补一个演示视频）

本人曾在Windows和Ubuntu均成功搭建此系统。

由于Vim学习难度大，如果不想折腾的朋友可使用Hexo + Visual Studio Code（搭配 `Markdown Preview Enhanced` 插件）使用。

**本文重点在于<big><u>搭建</u></big>，Hexo、Vim、Markdown等的相关知识不在本文中记录。可参考本人的《Hexo笔记》、《Vim笔记》、《Markdown笔记》。**

本人也在不断学习和不断摸索这套系统，如果大家有问题欢迎咨询联系我，我愿意共同探讨解决问题，联系方式在 `首页` -> `about` 页面。

<!-- more -->


<!-- vim-markdown-toc Redcarpet -->

+ [搭建思路](#搭建思路)
+ [1. 安装Hexo博客](#1-安装hexo博客)
    * [1.1 安装Git](#1-1-安装git)
    * [1.2 安装Nodejs](#1-2-安装nodejs)
    * [1.3 安装npm、cnpm](#1-3-安装npm、cnpm)
    * [1.4 安装Hexo](#1-4-安装hexo)
    * [1.5 Hexo建站](#1-5-hexo建站)
+ [2. Hexo日常使用](#2-hexo日常使用)
    * [2.1 新建及编辑文章](#2-1-新建及编辑文章)
    * [2.2 生成页面](#2-2-生成页面)
    * [2.3 部署](#2-3-部署)
    * [2.4 本地发布（调试）](#2-4-本地发布（调试）)
+ [3. 安装Vim](#3-安装vim)
    * [3.1 安装Vim](#3-1-安装vim)
    * [3.2 vimrc文件](#3-2-vimrc文件)
    * [3.3 安装插件管理器](#3-3-安装插件管理器)
    * [3.4 插件的安装与配置](#3-4-插件的安装与配置)
        - [Vim-markdown插件](#vim-markdown插件)
        - [vimwiki](#vimwiki)
        - [Markdown-preview插件](#markdown-preview插件)
+ [参考文章、视频](#参考文章、视频)
+ [---](#)
+ [---](#)
+ [---](#)
+ [---](#)
+ [---](#)
+ [未归档!!!!!!!!!!!!!!!](#未归档)
+ [图片路径问题](#图片路径问题)
    * [hexo s的路径(Online）](#hexo-s的路径-online）)
    * [vim插件MarkdownPreview路径(Offline)](#vim插件markdownpreview路径-offline)
    * [解决办法](#解决办法)
    * [后续解决思路](#后续解决思路)

<!-- vim-markdown-toc -->

---

# 搭建思路

* 安装Hexo（依赖Git、Nodejs）
* 安装Vim
* 安装Vim插件管理器
* 安装Vim插件

---

# 1. 安装Hexo博客

> [参考资料](https://hexo.io/zh-cn/docs/)

Hexo博客依赖Git和Nodejs环境，需要先安装Git和Nodejs。


## 1.1 安装Git

* Windows：下载并安装 [git](https://git-scm.com/download/win)。

* Mac：使用 [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) 或者下载 [安装程序](http://sourceforge.net/projects/git-osx-installer/)。

* Linux (Ubuntu, Debian)： `sudo apt-get install git-core`

* Linux (Fedora, Red Hat, CentOS)： `sudo yum install git-core`


## 1.2 安装Nodejs

> 建议安装LTS版本

* Windows：前往官网(https://nodejs.org/zh-cn/)下载并安装



## 1.3 安装npm、cnpm

安装npm和cnpm，设置国内下载源。


## 1.4 安装Hexo

在 控制台/终端 使用命令

```
npm install -g hexo-cli
```

如果下载速度很慢，可以使用cnpm

```
cnpm install -g hexo-cli
```

## 1.5 Hexo建站

```
hexo init [folder]
```

在当前目录下创建名为`folder`的文件夹（可改任意名），并在该文件夹下建立网站，会自动下载建站所需文件。如果没有填写`folder`，则在当前文件夹中建立网站。

> 下载过程较缓慢，建议掌握正确上网方法

下载成功后，使用`npm install`命令检查有否相关依赖包需要下载。

上述步骤完成后，Hexo的初始化工作便完成。

---

# 2. Hexo日常使用

关于Hexo使用的内容过多，这里只讲日常使用，更多内容请看《Hexo笔记》。

下方提及的所有命令，均在Hexo建站后的目录内进行，这里以`blog`为例。


## 2.1 新建及编辑文章

所有用户编写的文章均存放在`...\blog\source\_posts\`内

新建一个以title为文件名的md文件，即title.md

```
hexo new "title"
```

然后便可以使用编辑器进行内容编辑，完成后保存退出即可。

## 2.2 生成页面

文章发布前，需要先进行格式转换，Hexo能通过 `md` 文件生成为 html 页面。

**清理缓存**

> 其实是清理曾经生成过的Html页面

```
hexo clean
```

**生成页面**

```
hexo g
```

## 2.3 部署

Hexo创建的网站可以部署到私人服务器，或者Github、Gitee等网站，部署成功并上传网站后才可以在互联网访问。

根据个人喜好选择部署目的地，这里以Github、Gitee为例讲解。实际上，只需要部署到其一便可访问。

第一次部署需要在Github、Gitee创建项目仓库，以接收本地的Hexo生成的HTML网站文件。

（TODO: 补充Github、Gitee网站的项目创建，及与本地网站关联内容）

至此完成部署设置。

**部署命令**

```
hexo d
```

以后每次完成内容改动后，只需执行 `hexo d` 便会自动上传并更新HTML网站。


> 上传过程有时会要求输入对应网站的帐号、密码


## 2.4 本地发布（调试）

```
hexo s
```

启动本地服务。默认访问地址为 `http://localhost:4000` 。

服务启动后，会自动检测文件变动，可在此时进行文章编辑，及网站设置改动。改动后保存，并刷新网站可即时查看更新效果。通过这样，可以作为本地调试使用。

<++>

---

# 3. 安装Vim

## 3.1 安装Vim

我们为Windows和Linux分别记录

Win下，前往[Vim官网](https://www.vim.org/)下载并安装GVim


## 3.2 vimrc文件

Vim强大是因为它有很强大的自定义性，而vimrc则是主要的配置文件

不同系统它的文件名和存放路径不一样，Windows下是`_vimrc`，存放在安装目录下。

后面我们要在这个文件中加入的内容比较多，建议每次更改前先备份。

大部分内容我都已经注释，看注释就知道怎么设置了。

如果觉得内容太多不想看，直接到我Github上的vimrc文件，把内容复制进去保存即可。

（TODO: 补一个link，放上自动上传的最新的个人vimrc文件。）

**下面的内容是为了讲解，不要在这里复制，可能会有重叠的代码。**

* 基础设置

```
" Basic setting {{{

set nocompatible


" 在正文的左侧显示行数
set nu

" 把GVIM设为英文
let $LANG = 'en'  "set message language
set langmenu=en   "set menu's language of gvim. no spaces beside '='

set tabstop=4       " tab占4个空格
set softtabstop=4   " 设置expandtab的情况下，输入backspace删除的空格
set shiftwidth=4    "一般情况下tabstop=softtabstop=shiftwidth，这样不会乱

" 语法高亮
syntax on

" 更改文件编码
set encoding=utf-8
set langmenu=zh_CN.UTF-8
set fileencodings=ucs-bom,utf-8,cp936,gb18030,latin1
" 检测是否win系统(未测试)
if has("win32")
set fileencoding=chinese
else
set fileencoding=utf-8
endif

" 解决consle输出乱码
language message zh_CN.UTF-8

" 解决菜单乱码(未测试）
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim

" EK：使文件类型（即后缀名的文本字符串）被vim和plug可用
filetype on
filetype plugin on

" 设置窗口长宽度（以显示多少行、列来计算）
set lines=60 columns=108

" }}}

```

* 按键设置

```
" Keys setting{{{

" Set <LEADER> as <SPACE>
let mapleader = " "

" Markdown hotkey
source D:\Program Files\Vim\snippits.vim

" "运行"不同格格式的文件
" 参考：
"	https://www.bilibili.com/video/BV1ox411R7bo
"	https://github.com/theniceboy/.vim/blob/master/vimrc
map <leader>r :call CompileRunGcc()<CR>
func! CompileRunGcc()
  exec "w"
  if &filetype == 'c'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'cpp'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'java'
    exec "!javac %"
    exec "!time java %<"
  elseif &filetype == 'sh'
    :!time bash %
  elseif &filetype == 'python'
    silent! exec "!clear"
    exec "!time python3 %"
  elseif &filetype == 'html'
    exec "!firefox % &"
  elseif &filetype == 'markdown'
    exec "MarkdownPreview"
  elseif &filetype == 'vimwiki'
    exec "MarkdownPreview"
  endif
endfunc

map <leader>rr :call CompileRunGcc2()<CR>
func! CompileRunGcc2()
  exec "w"
  if &filetype == 'c'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'cpp'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'java'
    exec "!javac %"
    exec "!time java %<"
  elseif &filetype == 'sh'
    :!time bash %
  elseif &filetype == 'python'
    silent! exec "!clear"
    exec "!time python3 %"
  elseif &filetype == 'html'
    exec "!firefox % &"
  elseif &filetype == 'markdown'
    exec "MarkdownPreviewStop"
  elseif &filetype == 'vimwiki'
    exec "MarkdownPreviewStop"
  endif
endfunc

" }}}
```

13行、39行，设置了两个function（还是叫函数?），功能是按`空格r` 打开Markdown预览生成的页面，按`空格rr` 关闭预览。



* 自定Markdown快捷输入

> 这个内容是可选项，根据个人习惯考虑是否使用。

由于内容较多，我们先在vimrc文件中加入`source D:\Program Files\Vim\snippits.vim` ，路径可自定，但是建议放在安装路径内，以免平时清理垃圾文件时误删除。

这行命令的意思是vimrc可以加载外部的命令行，**简单点说就是内容太多了，再开一个文件放置。**

然后我们在这个路径下创建一个`snippits.vim` ，写入下面的内容，每一行的作用我都已经注释了意思。

下面的内容是复制自一位大佬TheCW的VIM配置的，有兴趣的朋友可以看看他的视频。


```
" 参考：
"     TheCW视频：《不影响听课的高效率记笔记方法：Vim + Markdown - 教学与配置》
"     https://www.bilibili.com/video/BV1ox411R7bo

" 弃用？暂时看不懂
"autocmd Filetype markdown map <leader>w yiWi[<esc>Ea](<esc>pa)

" 在插入模式下输入 ",f" ，跳转到下一个定位符并删除这个定位符
autocmd Filetype markdown inoremap ,f <Esc>/<++><CR>:nohlsearch<CR>c4l

" 在插入模式下输入 ",b" ，输入 "粗体" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,b **** <++><Esc>F*hi

" 在插入模式下输入 ",s" ，输入 "删除线" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,s ~~~~ <++><Esc>F~hi

" 在插入模式下输入 ",i" ，输入 "斜体" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,i ** <++><Esc>F*i

" 在插入模式下输入 ",d" ，输入 "行内代码块" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,d ``<++><Esc>F`i

" 在插入模式下输入 ",c" ，输入 "代码块" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,c ```<Enter><++><Enter>```<Enter><Enter><++><Esc>4kA

" 在插入模式下输入 ",h" ，输入 "高亮" 格式和用于跳出的 "定位符"
" EK：下面这行在初始的Markdown不支持，不能高亮，所以我改成了用html语法的。
" autocmd Filetype markdown inoremap ,h ====<Space><++><Esc>F=hi
autocmd Filetype markdown inoremap ,h <mark></mark><Space><++><Esc>F<i

" 在插入模式下输入 ",p" ，输入 "图片" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,p ![](<++>) <++><Esc>F[a

" 在插入模式下输入 ",a" ，输入 "超链接" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,a [](<++>) <++><Esc>F[a

" 在插入模式下输入 ",1" ，输入 "标题一" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,1 #<Space><Enter><++><Esc>kA

" 在插入模式下输入 ",2" ，输入 "标题二" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,2 ##<Space><Enter><++><Esc>kA

" 在插入模式下输入 ",3" ，输入 "标题三" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,3 ###<Space><Enter><++><Esc>kA

" 在插入模式下输入 ",4" ，输入 "标题四" 格式和用于跳出的 "定位符"
autocmd Filetype markdown inoremap ,4 ####<Space><Enter><++><Esc>kA

" 在插入模式下输入 ",l"（英文l），输入 "--------<Enter>"
autocmd Filetype markdown inoremap ,l --------<Enter>

" 在插入模式下输入 ",n" 为插入分隔线
autocmd Filetype markdown inoremap ,n ---<Enter><Enter>
```

这里重点讲一下“定位符”是什么意思，这个词是我自己定的。

举一个例子大家就明白了，平时我们要输入Markdown的**粗体**，需要以下步骤：

1、 输入`**`	显示：`**`

2、 输入`内容`	显示： `**内容`

3、 输入`**`	显示：`**内容**`

而使用了上面的设置之后

1、 输入`,b`	显示：`**** <++>`，并且光标自动移动到四个*号中间等待输入内容

2、 输入`内容`	显示：`**内容** <++>`

3、 输入`,f`	显示：`**内容** `，并且光标自动跳到原来的 `<++>`位置上

其它所有格式都是这个原理，`,f`的作用就是：跳转到定位符的位置，并删除这个定位符。


## 3.3 安装插件管理器

安装主流的插件管理器`vim-plug`

[Github vim-plug](https://github.com/junegunn/vim-plug)

* 安装方法

可以使用手动下载法，或者是Github主页上的命令安装法。

手动下载：下载`plug.vim`文件存放到windows下的 `$HOME/vimfiles/autoload/plug.vim` 路径。（如果是Unix系统则放在 `~/.vim/autoload/plug.vim`）

命令安装：看上方的Github主页，直接复制命令运行即可。

* 配置方法

在vimrc文件中写入下方代码

```
call plug#begin('~/.vim/plugged')

call plug#end()
```

这是一个`vim-plug`区域，第一行begin开始，第三行end结束。

第一行中的`~/.vim/plugged`是后续安装插件的目录，可自行更改到需要的位置。

第一和第三行中间用于填入需要安装的插件，可插入多行。

例如我要安装5个插件

```
"
" 插件管理器 {{{
"

call plug#begin('~/.vim/plugged')

" Markdown-preview插件
" 链接：https://github.com/iamcco/markdown-preview.nvim
Plug 'iamcco/markdown-preview.nvim', { 'do': { -> mkdp#util#install() }, 'for': ['markdown', 'vim-plug']}

" Markdown插件
Plug 'godlygeek/tabular'
Plug 'plasticboy/vim-markdown'

" paste image into vim
Plug 'ferrine/md-img-paste.vim'

" vimwiki
Plug 'vimwiki/vimwiki'

call plug#end()
" }}}
```

插件加入安装的格式 `Plug '插件名'`，插件名的获取需要到插件的官网上找。

* 插件安装

进入vim

输入`:PlugUpgrade`可以检查vim-plug有否升级

输入`:PlugStatus`可查看当前加入到vimrc中插件的安装情况

当我们看到输入有尚未安装的插件，可以执行`:PlugInstall`命令，开始进行插件的安装。此时需耐心等待，安装完成后会有提示。重启vim即可使用完成安装的插件。

* 插件更新

输入`:PlugUpdate` 会自动开始更新已列入的插件

* 插件删除

进入vimrc文件，把不需要的插件所在行删除。

然后打开vim，输入`:PlugClean`会自动删除不在`vimrc`列表的插件。

## 3.4 插件的安装与配置

TODO: 加插件的安装教程

插件列表如下：

```
" vimwiki，一个笔记管理和跳转插件
Plug 'vimwiki/vimwiki'   
```

下面逐个插件进行简单讲解

### Vim-markdown插件

[Github地址]()

> 这个插件好像没什么用？

让vim提供markdown相关的支持

vimrc中的个人设置

```
" 插件安装
call plug#begin('~/.vim/plugged')
Plug 'godlygeek/tabular'
Plug 'plasticboy/vim-markdown'
call plug#end()

"
" Vim-markdown 插件设置 {{{
"
let g:vim_markdown_folding_disabled = 1 """"设置不做代码折叠
let g:vim_markdown_frontmatter=1 "" 设置支持yaml语法
let g:vim_markdown_math = 1    " 打开latex支持
}}}
```

* 命令详解

对齐和补全已存在的r*表格**
```
:TableFormat
```

### vimwiki

[vimwiki官网](https://github.com/vimwiki/vimwiki)
[vimwiki中文网址](https://github.com/vimwiki/vimwiki/blob/master/README-cn.md)

一个提供笔记统一管理和跳转功能的插件

第一次使用要在vimrc文件中添加设置

```
"
" vimwiki plug setting {{{
"

" 设定默认初始路径，同时改变vimwiki默认的格式（从wiki后缀名改为md）
let g:vimwiki_list = [{'path': 'D:\WorkSpace\Hexo\blog\source\_posts',
                      \ 'syntax': 'markdown', 'ext': '.md'}]
" }}}
```

这里的`D:\WorkSpace\Hexo\blog\source\_posts`应改为实际在本地部署Hexo网站文件夹下的_posts路径

设置完成后，我们只需要在vim中输入`<Leader>ww`（\<Leader\>默认是`\`键），即可打开_posts路径下的index.md文件

此文件可以理解为类似Linux根目录的根文件

下面做个例子就能明白了

在此文件中输入以下内容

```
= 我的vimwiki笔记系统 =

# IT

	## Coding
	Python笔记
	C++笔记
	Java笔记
	
	## 操作系统
	
		### Linux
		Linux笔记

# Math

	## 代数
	高一代数
	高二代数
	高三代数
	
	## 几何
	初一几何
	初二几何
	初三几何

# English
雅思笔记
托福笔记
```

假如我们一开始要做的笔记是这些（实际是可以逐渐增加的，这里为是演示所以构建了这样一个框架）

现在我们要编辑`Python笔记`，我们要先选中“Python笔记”的所有字体，然后按Enter键

这样，vimwiki就会自动生成一个`Python笔记.md`的文件，并进入其中，可以马上编辑并自动保存

在编辑完成后，我们可以按退格键回到`index.md`。

下次需要进行编辑时，只需要将光标移动到`Python笔记`中的其中一个字上面，按回车就可以进入。

### Markdown-preview插件

[Github主页](https://github.com/iamcco/markdown-preview.nvim)

一款可以在**编辑的同时同步预览**Markdown生成页面的插件

个人在vimrc中加入了下面的代码，按`<leader>r` 取代原命令`:MarkdownPreview`，打开同步预览功能。

有时不小心关闭了预览页面，不能再次打开。是因为上次退出没有使用`MarkdownPreviewStop`命令关闭，执行一次此命令即可恢复。

```
" “运行”不同格格式的文件
"	https://www.bilibili.com/video/BV1ox411R7bo
"	https://github.com/theniceboy/.vim/blob/master/vimrc
" 按<leader>r 运行
map <leader>r :call CompileRunGcc()<CR>
func! CompileRunGcc()
  exec "w"
  if &filetype == 'c'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'cpp'
    exec "!g++ % -o %<"
    exec "!time ./%<"
  elseif &filetype == 'java'
    exec "!javac %"
    exec "!time java %<"
  elseif &filetype == 'sh'
    :!time bash %
  elseif &filetype == 'python'
    silent! exec "!clear"
    exec "!time python3 %"
  elseif &filetype == 'html'
    exec "!firefox % &"
  elseif &filetype == 'markdown'
    exec "MarkdownPreview"
  elseif &filetype == 'vimwiki'
    exec "MarkdownPreview"
  endif
endfunc

" 按<leader>rr停止
map <leader>rr :call CompileRunGcc2()<CR>
func! CompileRunGcc2()
  exec "w"
  if &filetype == 'markdown'
    exec "MarkdownPreviewStop"
  elseif &filetype == 'vimwiki'
    exec "MarkdownPreviewStop"
  endif
endfunc
```
---

# 参考文章、视频

[Hexo官网](https://hexo.io/zh-cn/docs/)（建议看英文版的，中文版不如英文版的资料新）

[无火老大哥：《高效做笔记:vim + markdown》](https://zhuanlan.zhihu.com/p/84773275)

[TheCW视频：《不影响听课的高效率记笔记方法：Vim + Markdown - 教学与配置》](https://www.bilibili.com/video/BV1ox411R7bo)

# ---
# ---
# ---
# ---
# ---

# 未归档!!!!!!!!!!!!!!!

> 下面内容为散装内容，未整理入文章中

# 图片路径问题

如何统一，能够实现既能够在MarkdownPreview显示图片，也能在hexo s中显示图片

> 有兴趣可以看看 [Hexo载入多媒体内容原理](https://hexo.io/zh-cn/docs/asset-folders.html)

## hexo s的路径(Online）

**默认情况**

```
使用 ![](images/test.jpg) 引用
```

用户编辑的一切文件都应该放在`source`文件夹中

所以我们可以把图片放入`source`文件夹中的任意位置，然后在文章中引用。

例如把图片（这里举例是`test.jpg`）放入`blog/source/images` 下 （“images”可以改为其它名称）

然后在md文件中，使用`![](images/test.jpg)` 完成图片引用。

---

**第二种情况**

```
使用`![](test.jpg)` 引用
```

Hexo提供了第二种引用方法，就是通过安装一个hexo插件 [xcodebuild/hexo-asset-image](https://github.com/xcodebuild/hexo-asset-image)（现在的版本好像都已经自带安装好了）

安装命令： `npm install hexo-asset-image --save`

同时在博客根目录下，把 `_config.yml` 文件中的 `post_asset_folder` 属性改为 `true`

这样就可以把的图片存放到 `source/_posts/` 目录内，且与文章同名的目录下。同时使用 `![](test.jpg)` 方式引用了。

> 例如我要在文章《Hexo笔记》下插入图片“Hexo框架.jpg”，我只需要把图片存放在与《Hexo笔记》同级的文件夹“Hexo笔记”目录下，然后在文章中使用 `![](Hexo框架.jpg)` 即可成功插入。

## vim插件MarkdownPreview路径(Offline)

```
使用绝对路径
![](/Home/用户名/Document/Hexo/blog/source/_posts/文件夹名/test.jpg)
使用相对路径
![](./文件夹名/test.jpg)
```

## 解决办法

暂时没有很好的解决办法。不是办法的办法就是用`hexo s`的格式来做笔记，这样就不能在MarkdownPreview中预览了。

这样做是因为平时插入图片不算多，用`hexo s`命令预览，麻烦一点但是也能用。并且要发布的话，也只能用`hexo s`能识别的格式。如果用MarkdownPreview的格式输入，发布后图片就显示不出来了。

## 后续解决思路

找MarkdownPreview负责识别图片路径的设置文件，更改识别格式（或者找Hexo中同样的文件）。目的是将两者统一。（考虑一下改哪个好？）













