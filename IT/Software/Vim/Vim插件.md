---
title: Vim插件
tags:
  - Vim
  - Plug
  - 插件
categories:
    - [+IT, Software, Vim]
date: 2020-08-02 18:08:26
---

# Table of Content


<!-- vim-markdown-toc Redcarpet -->

+ [插件管理器](#插件管理器)
	* [vim-plug](#vim-plug)
+ [插件](#插件)
	* [外观类](#外观类)
		- [lightline.vim状态栏插件](#lightline-vim状态栏插件)
		- [vim-airline状态栏插件](#vim-airline状态栏插件)
		- [vim-snazzy配色插件](#vim-snazzy配色插件)
	* [未分类](#未分类)
		- [vimwiki插件](#vimwiki插件)
			+ [Key Shortcuts](#key-shortcuts)
			+ [Commands](#commands)
		- [vim-markdown插件](#vim-markdown插件)
		- [Markdown-preview插件](#markdown-preview插件)
		- [easymotion插件](#easymotion插件)
		- [vim-markdown-toc插件](#vim-markdown-toc插件)
			+ [Commands](#commands)
			+ [Options](#options)

<!-- vim-markdown-toc -->


<!-- more -->

---

# 插件管理器

## vim-plug

[Github vim-plug](https://github.com/junegunn/vim-plug)

* 安装方法

下载`plug.vim`文件到vim下的`autoload`目录里面即可

下载方法，可以到Github主页上直接下载；也可以按照Github主页上的命令行执行命令

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


# 插件

<font size=5>以下内容为本人用过的插件的使用记录。</font>

## 外观类

### lightline.vim状态栏插件

[Link](https://github.com/itchyny/lightline.vim)

一款状态栏插件，能清晰显示出当前模式、文件名、光标所在的行列值等信息，能根据喜好更换官方提供的主题。装上就能用，未深入研究设置。

* Installation
```VimScript
 Plug 'itchyny/lightline.vim'
```

--------

<br>

### vim-airline状态栏插件

> 在lightline.vim状态栏插件首页好像说这个airline插件依赖太多其他Vim的功能，或其它插件。我个人在Windows下使用过程中偶有报错，并且对比lightline.vim之后，觉得lightline.vim确实如作者所说的更简洁、轻量。所以转去使用lightline.vim了。

和lightline.vim状态栏插件一样，能显示出当前模式、文件名、光标所在的行列值等信息，能根据喜好更换官方提供的主题。装上就能用，未深入研究设置。


--------

<br>

### vim-snazzy配色插件

> 其实只是一个配色文件，只是可以通过插件形式安装。

[Link](https://github.com/connorholyday/vim-snazzy)

一款很好看的Vim配色插件。

* Installation
```VimScript
Plug 'connorholyday/vim-snazzy'
```


安装完成后，使用`:colorscheme snazzy`更改配色。如果需要每次打开Vim自动使用本配色文件，则需要在`vimrc`文件中定入`colorscheme snazzy`保存。

* Manually Install

也可以不用插件管理器安装，直接在github下载配色文件`snazzy.vim`，放到Vim的配色文件目录 `~/.vim/colors/`，如果是Windows则是在 `<your-vim-dir>\vimfiles\colors\`。

> Windows用插件管理器安装，并配置好vimrc文件后，如果每次运行都报错“没有找到该配色文件”，可用手动安装方法，把配色文件放置在`<your-vim-dir>\vimfiles\colors\`目录。

* 背景透明

```VimScript
let g:SnazzyTransparent = 1
```

> 貌似在Windows下不可用。

--------

<br>


## 未分类

### vimwiki插件

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

这里的`path` `D:\WorkSpace\Hexo\blog\source\_posts`可根据需要进行更改。

设置完成后，我们只需要在vim中输入`<leader>ww`（\<leader\>默认是`\`键），即可进入vimwiki开始使用。

vimwiki会自动在上面设定的`path`下创建一个index.md文件，可以把这个文件理解成是索引目录，或者是理解为Linux的根目录。

下面做个例子就能明白了

我们在此文件构建下方的知识体系，输入以下内容进这个`index.md`文件。

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

现在我们要编辑`Python笔记`，我们要先选中“Python笔记”的所有字体，然后按Enter键

这样，vimwiki就会自动生成一个`Python笔记.md`的文件，并打开文件准备编辑。

当我们完成这个笔记的内容记录（编辑完成）后，我们可以按退格键(Backspace)，vimwiki就会回到`index.md`。

下次需要进行编辑时，只需要将光标移动到`Python笔记`中的其中一个字上面，按回车就可以进入继续编辑。

* vimwiki生成的新文档，与`index.md`同目录。
* vimwiki打开文件是检索同目录下有没有该文件名，有就打开，没有就创建。（意味着文件间没有层级关系，可以随意调用）



#### Key Shortcuts

normal 模式:

* `<Leader>ww` -- 进入vimwiki（打开默认的 wiki 目录文件）
* `<Leader>wt` -- 在新标签（Tab）中打开 wiki 目录文件
* `<Leader>ws` -- 在多个 wiki 中选择并打开该 wiki 的目录文件
* `<Leader>wd` -- 删除当前 wiki 文件
* `<Leader>wr` -- 重命名当前 wiki 文件
* `<Enter>` -- 创建或打开 wiki 链接
* `<Shift-Enter>` -- 先上下分屏再打开 wiki 链接（若非链接则先创建）
* `<Ctrl-Enter>` -- 先左右分屏再打开 wiki 链接（若非链接则先创建）
* `<Backspace>` -- 返回之前浏览的 wiki 文件
* `<Tab>` -- 跳到本文件中下一个 wiki 链接
* `<Shift-Tab>` -- 跳到本文件中上一个 wiki 链接

更多快捷键说明，请阅 `:h vimwiki-mappings`


#### Commands

```
:VimwikiTOC
```

在文章顶部生成TOC

> EK：不好用。只能在Vim和vimwiki下跳转，Hexo生成的网页无效。

---


### vim-markdown插件

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

* Commands

对齐和补全已存在的**表格**
```
:TableFormat
```

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

### easymotion插件

快速把光标跳转、定位到指定位置

[PegasusWang视频《vim easymotion 瞬间移动大法》](https://www.bilibili.com/video/BV1mE411t76N)


### vim-markdown-toc插件

一个可在光标当前位置自动生成目录(`Tablc of Content`，缩写`TOC`)的插件，可以跳转、自动更新。

> 现阶段使用主要因为有两点需求：①手机访问Hexo没有TOC显示，无法跳转；②Vim编辑没有TOC，看不到大纲框架，难以编辑（vim-markdown插件有看TOC的功能，学习这个插件，看能否替代）

> 解决上面两个问题后，可以不用这个插件。（因为和vimwiki有点小冲突?）

[Github主页](https://github.com/mzlogin/vim-markdown-toc)

[中文说明](https://mazhuang.org/2015/12/19/vim-markdown-toc/)

#### Commands

* 生成目录

根据不同的Markdown渲染引擎，共有两条生成目录的命令。

```
:GenTocGMF
```

**GFM**：适用于 GitHub 仓库里的 Markdown 文件，比如 README.md，也适用用于生成 GitBook 的 Markdown 文件。

```
:GenTocGitLab
```

**GitLab**：

Generate table of contents in [GitLab](https://docs.gitlab.com/ee/user/markdown.html) link style.

This command is suitable for GitLab repository and wiki.

```
:GenTocRedcarpet
```

**Redcarpet**：适用于使用 Redcarpet 作为 Markdown 引擎的 Jekyll 项目或其它地方。

* 更新目录

```
:UpdateToc
```

Generally you don't need to do this manually, existing table of contents will auto update on save by default.

The `:UpdateToc` command, which is designed to update toc manually, can only work when `g:vmt_auto_update_on_save` turned off, and keep insert fence.

> EK: `fence` 是指Table of Contents 前后的 `<!-- vim-markdown-toc -->`

* 删除目录

```
:RemoveToc
```

#### Options

```Vim Script
" This plugin will update existing table of contents on save automatic.
" default: 1
let g:vmt_auto_update_on_save = 1

" By default, the :GenTocXXX commands will add <!-- vim-markdown-toc --> fence to the table of contents, it is designed for feature of auto update table of contents on save and :UpdateToc command..
" default: 0
let g:vmt_dont_insert_fence = 0

" 生成的TOC，无论是第几级的标题，默认是*号开头。如果下面这个option值改为“1”，则1、2、3级标题的开头分别是 * - + 。
" default: 0
let g:vmt_cycle_list_item_markers = 0

" 标题前的符号，默认是*，可改为 * - + 其中一个。
let g:vmt_list_item_char = "*"

" Include headings before the position you are inserting Table of Contents.
" default: 0
let g:vmt_include_headings_before = 0
```



--------

<br>

