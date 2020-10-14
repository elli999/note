---
title: Hexo笔记
date: 2020-05-15 00:47:04
tags: 
    - hexo
    - 笔记方法学
    - 笔记
    - note
categories:
	- [笔记方法学]
	- [+IT, Software, Hexo]
---

My Hexo wiki.

# Table Of Content


<!-- vim-markdown-toc Redcarpet -->

+ [Hexo目录结构](#hexo目录结构)
	* [.deploy](#deploy)
	* [node_modules](#node_modules)
	* [public](#public)
	* [scaffolds](#scaffolds)
	* [source](#source)
		- [_drafts](#drafts)
		- [_posts](#posts)
	* [themes](#themes)
	* [_config.yml](#config-yml)
	* [package.json](#package-json)
+ [按需求分类](#按需求分类)
	* [Hexo新建文章](#hexo新建文章)
	* [更换主题](#更换主题)
	* [增加网站访问量统计功能](#增加网站访问量统计功能)
	* [增加评论区](#增加评论区)
	* [增加搜索功能 （重要！！！）](#增加搜索功能-（重要！！！）)
	* [插入本地图](#插入本地图)
	* [使用mermaid](#使用mermaid)
+ [Bug记录](#bug记录)
	* [显性Bug](#显性bug)
		- [在#做的标题里，不要用`{`、`}`](#在-做的标题里，不要用-、)
	* [隐性Bug](#隐性bug)
		- [首页不显示文章](#首页不显示文章)
		- [文章404](#文章404)
		- [图片不显示](#图片不显示)
		- [文章乱码](#文章乱码)
+ [---](#)
+ [---](#)
+ [---](#)
+ [---](#)
+ [---](#)
+ [弃？(((](#弃？)
+ [文章属性](#文章属性)
	* [4.1.1.1. layout](#4-1-1-1-layout)
	* [4.1.1.2. title](#4-1-1-2-title)
	* [4.1.1.3. date](#4-1-1-3-date)
	* [4.1.1.4. updated](#4-1-1-4-updated)
	* [4.1.1.5. comments](#4-1-1-5-comments)
	* [4.1.1.6. tags](#4-1-1-6-tags)
	* [4.1.1.7. categories](#4-1-1-7-categories)
	* [4.1.1.8. permalink](#4-1-1-8-permalink)
	* [4.1.1.9. description?](#4-1-1-9-description)
	* [4.2. 生成静态页面](#4-2-生成静态页面)
	* [4.3. 在本地建立服务（预览）](#4-3-在本地建立服务（预览）)
	* [4.4. 部署到服务器](#4-4-部署到服务器)
+ [弃？)))](#弃？)

<!-- vim-markdown-toc -->

<!-- more -->

--------------------------------------------------------------------------------------------------------

# Hexo目录结构

补图

* .deploy
* node_modules
* public
* scaffolds
* source
    * \_drafts
    * \_posts
* theme
* \_config.yml
* package.json

## .deploy

需要部署的文件

## node_modules

hexo插件

## public

**生成的静态网页文件**：当使用hexo generate命令时，hexo会从source中把所有内容生成为静态网页文件并存放在此文件夹。即此文件夹便是完整的网站内容，后续使用hexo deploy部署时，也是只上传这个文件夹。

## scaffolds

[模版](https://hexo.io/zh-cn/docs/writing) 文件夹。当您新建文章时，Hexo会根据 scaffold 来建立文件。

</br>

Hexo的模版是指在新建的文章文件中默认填充的内容。例如，如果您修改 scaffold/post.md中的 Front-matter 内容，那么每次新建一篇文章时都会包含这个修改。

## source

**生成静态网页前的源文件**：如md文件、图片文件、404、favicon、CNAME等。使用hexo new命令生成的md文件便是存放于此。后续使用hexo generate时便把内容转化为静态网页文件，保存在public文件夹。

### _drafts

草稿

### _posts

文章

## themes

Hexo的主题目录：把从网上下载的Hexo主题放在这里，并在全局 \_config.yml 配置文件中将 theme： xxxx 改为对应的新主题名，就会成功更改主题。（“xxxx” 的内容要和 theme 文件夹内的主题文件夹名字相同）

## _config.yml

网站的 [配置](https://hexo.io/zh-cn/docs/configuration) 信息，您可以在此配置大部分的参数。

> EK： 全局配置文件：在这里可以更改如主题、部署目标地址、网站名、拥有者名等内容。


| 参数        | 描述                                                                                                                                                 |
| :---:       | :---:                                                                                                                                                |
| title       | 网站标题                                                                                                                                             |
| subtitle    | 网站副标题                                                                                                                                           |
| description | 网站描述                                                                                                                                             |
| keywords    | 网站的关键词。使用半角逗号 , 分隔多个关键词。                                                                                                        |
| author      | 您的名字                                                                                                                                             |
| language    | 网站使用的语言。对于简体中文用户来说，使用不同的主题可能需要设置成不同的值，请参考你的主题的文档自行设置，常见的有 zh-Hans和 zh-CN。                 |
| timezone    | 网站时区。Hexo 默认使用您电脑的时区。请参考 时区列表 进行设置，如 America/New_York, Japan, 和 UTC 。一般的，对于中国大陆地区可以使用 Asia/Shanghai。 |

其中，`description`主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。author参数用于主题显示文章的作者。

## package.json

应用程序的信息。[EJS](https://ejs.co), [Stylus](learnboost.github.io/stylus/) 和 [Markdown](https://daringfireball.net/projects/markdown/) renderer 已默认安装，您可以自由移除。

```
package.json

{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": ""
  },
  "dependencies": {
    "hexo": "^3.8.0",
    "hexo-generator-archive": "^0.1.5",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-index": "^0.2.1",
    "hexo-generator-tag": "^0.2.0",
    "hexo-renderer-ejs": "^0.3.1",
    "hexo-renderer-stylus": "^0.3.3",
    "hexo-renderer-marked": "^0.3.2",
    "hexo-server": "^0.3.3"
  }
}
```

--------------------------------------------------------------------------------------------------------

<br>

# 按需求分类

## Hexo新建文章

有两种方法：

**方法一：**

在网站目录下使用`hexo new "文章名"`进行新建文章，hexo会自动在`_posts`文件夹下生成`文章名.md`文件，文件已自带post的模板内容（默认带有`Front-matter`内容）。


**方法二：**

直接复制或者新建md文件放入 `_posts` 文件夹内，但是要自己补上`Front-matter`。

> Hexo貌似不能识别带有空格的md文件名（例如：`Linux - 日常使用.md`，现在已全部统一不用空格，变成`Linux-日常使用.md`）。使用文件名带空格的md文件，在生成文章后在首页不显示文章（但是貌似在分类中可以找到）。原因应该是因为生成的URL中间不能含有空格，而Hexo默认是调用文件名生成URL的，所以Hexo发现空格后会自动改为 `-` ，例如把`hexo new "Visual Studio Code笔记`命令对应生成的md文件改为`Visual-Studio-Code笔记`。

---

## 更换主题

见上方目录结构章节中的 theme 文件夹讲解

---

## 增加网站访问量统计功能

利用“不蒜子”提供的服务： ibruce.info/2015/04/04/busuanzi/

注：其它也可以，可以找同类的替代品。但是静态网站本身无法完成动态内容，必须要借助类似这种外来服务才能增加诸如统计计数、评论等功能。

---

## 增加评论区

> 好像需要备案，不然有人发布不良言论会影响网站。

1、 Disqus（被墙）
2、 来必力 livere.com
3、 多说（好像没了）
4、 畅言 changyan.kuaizhan.com

---

## 增加搜索功能 （重要！！！）

1、 swiftype.com （好像收费了）

原理：在你注册后，它就爬虫你的网站所有内容，建立索引在自己的服务器

2、 自定义 site 语法进行跳转

原理： 相当于在搜索引擎输入 “ site:taobao.com 铅笔“，前提是这个搜索引擎已经收录了你的内容（爬取）

---

## 插入本地图

**方法一：**

把图片（这里举例是test.jpg）放入blog/source/images 下 （“images”可以改为其它名称）

> 应该只要放入source文件夹下任意位置都可以，这里放入`source\images`只是为了方便统一管理

在md文件中，使用`![](images/test.jpg)` 完成插入

**方法二：**

在 `_config.yml` 把`post_asset_folder`设为`true`，然后把当前文章所用的图片，保存到文章所在目录下的同名文件夹下，最后用 `![](图片文件名.jpg)` 方式引用即可。

> `_config.yml`在网站的根目录下，是Hexo的主配置文件，一般不要随便改动。

---

## 使用mermaid

> **What's mermaid?**
> 一个用Javascript开发，可以结合在Markdown里面，把代码渲染成各种图表的工具。
> 详见官方链接（主要看演示图，知道可以做什么就行）：
> https://github.com/mermaid-js/mermaid
> 官方文档：https://mermaid-js.github.io/mermaid/#/flowchart
> mermaid包含Flowchart流程图、Sequence Diagram序列图、Gantt甘特图、Class Diagram、State Diagram、Pie Chart饼状图等。

**Hexo使用mermaid的思路：**

由于我们可以安装各种各样的主题，而主流主题如next我在设置文件中找到是支持mermaid的，国产主题fluid也在自己的主页注明支持mermaid。所以可以推测主流的主题，一般是已经提供了mermaid的使用支持的。

在网上看到很多教程大部份是教通过安装插件解决，由于我个人没使用过对应插件，且主题已经支持的情况下，暂时我决定使用主题自带的mermaid渲染功能（因为担心插件可能会带来兼容性问题，及报错等现象）。

> 后来发现使用next主题自带的，语法格式和传统的不一样，Vim下的"MarkdownPreview"插件不能预览。

如果需要使用插件，我看到比较多网友推荐使用的两个插件分别是[hexo-filter-mermaid-diagrams](https://github.com/webappdevelp/hexo-filter-mermaid-diagrams) 和[hexo-filter-flowchart](https://github.com/bubkoo/hexo-filter-flowchart) ，网上有很多教程，使用其中一个即可。

**主题自带的mermaid使用方法：**

由于我个人是使用`next`主题的，下面以这个主题为例说明。

在Hexo搭建的网站下找到`theme\next\_config.yml`文件（该文件是主题的配置文件）。文件内搜索`mermaid`，得到以下内容。

```
# ---------------------------------------------------------------
# Tags Settings
# See: https://theme-next.js.org/docs/tag-plugins/
# EK：个人理解，这个Tag不是Front-matter里面的文章属性tag，而是使用标签方法来在文章中插入其它多媒体类型的元素，例如插入视频{% youtube video-id %}、代码块、PDF、Mermaid等，详见上link。
# ---------------------------------------------------------------

# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  transition:
    tabs: false
    labels: true

# PDF tag
# NexT will try to load pdf files natively, if failed, pdf.js will be used.
# So, you have to install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# See: https://github.com/next-theme/theme-next-pdf
pdf:
  enable: false
  # Default height
  height: 500px

# Mermaid tag
mermaid:
  enable: true
  # Available themes: default | dark | forest | neutral
  theme: forest
```

可以看到这是一个next带有的，名叫`Tags`的套件。默认的`mermaid`的`enable`属性为`false`，把它改为`true`。下面的`theme`是mermaid的主题，可理解为配色方案。

> 顶部提供了一个使用文档的网址[https://theme-next.js.org/docs/tag-plugins/](https://theme-next.js.org/docs/tag-plugins/)，可自行查阅。

现在可以在md文档中使用mermaid了。

引用格式如下：

```
{% mermaid type %}

内容

{% endmermaid %}
```

其中`type`是需要填写的，根据使用的图表不同，可根据需要填写`graph TD`、`graph LR`、`sequenceDiagram`、`gantt`、`classDiagram`、`stateDiagram`、`pie`、`journey`等。具体使用语法看我后面写的“Mermaid笔记”。（TODO：如何加超链？！）



---

<br>

# Bug记录

## 显性Bug

> 显性Bug即不可以使用，使用前就报错。

### 在#做的标题里，不要用`{`、`}`

在#做的标题里，不要用`{`、`}`，会导致`hexo g`失败。

> 看报错代码，应该是生成HTML页面时，`{`、`}`会混入HTML代码中。

---

<br>

## 隐性Bug

> 隐性Bug即可以使用，不报错，但是用的时候发现问题。

### 首页不显示文章

* 文章命名

Hexo貌似不能识别带有空格的md文件名（例如：`Linux - 日常使用.md`，现在已全部统一不用空格，变成`Linux-日常使用.md`）。使用文件名带空格的md文件，在生成文章后在首页不显示文章（但是貌似在分类中可以找到）

后续：使用`hexo new "Visual Studio Code笔记`生成新的笔记时，发现Hexo生成的文件名为`Visual-Studio-Code笔记.md`，但是可以在Hexo Server中见到文章，文章名为正常显示的`Visual Studio Code笔记`。同时打开链接后发现地址为`http://localhost:4000/2020/08/18/Visual-Studio-Code笔记/`。

推测结论：印象中，从来没有见过网址是带有空格的，而Hexo的工作原理是把`example.md`直接转换为同名的`example`的文件夹，同时在该文件夹下生成内容与md文件相同的`index.html`文件，以及把md文件引用的附件（图片）复制进去

下面以`example.md`为例

因为URL不能带有空格

{% mermaid graph LR %}
    A[example.md]
    B{文件名中是否含有空格}
    C(原文件名<不变>)
    D(空格改为减号)
    A --> B
    B -->|无空格| C
    B -->|有空格| D
{% endmermaid %}

---


### 文章404

在本地`hexo s`可以正常显示，但是deploy之后打开对应文章404，检查本地和服务器均存在该文章的index.html文件，但就是404显示不了。重新hexo clean 、 hexo g也不行。

**解决办法：**把文章日期改了一下，再重新`hexo clean && hexo g -d`就可以了。（因为生成的网站里面的文章是按日期分的文件夹路径，所以我的思路是改变日期，相当于改了该文章的路径再重新上传）

<mark>找不到原因。</mark>

---


### 图片不显示

1. 图片文件名不能有空格

> 出现版本：hexo-cli:3.1.0、node:12.16.3

例如`![VSC powershell](VSC powershell.png) `，这样显示不了。

解决方案：
* 可以用驼峰命名
* 用下划线 `_` 替代空格。
* 用HTML格式插入图片（未试，应该可以）

---

### 文章乱码

如果只是一篇文章乱码，应该是因为文章的编码格式不对，把它改为utf-8即可。

---

<br>

# ---
# ---
# ---
# ---
# ---


# 弃？(((

# 文章属性

文章属性在 `hexo new xxx` 生成 md 文件时自动创建，在文章头部，包含layout、title、date、updated、comments、tags、categories、permalink属性，其中有部分属性是有default值的，即默认初始属性，如果不改动则以default值为准。

一般格式如下：
```
---
title: Hexo部署笔记
date: 2020-05-15 00:47:04
categories:
    - Hexo
tags:
    - hexo
    - 笔记方法学
    - 笔记
    - note
---
```

部分属性如有需要可自行添加

## 4.1.1.1. layout

## 4.1.1.2. title

## 4.1.1.3. date

Published date

> **Default**： File created date

## 4.1.1.4. updated

Updated date

> **Default**: File updated date

## 4.1.1.5. comments

Enables comment feature for the post

> **Default**: true

## 4.1.1.6. tags

定义文章的标签属性 ( Not available for pages )

按如下格式填写即可

```
tags:
    - tag1
    - tag2
    - ...
```

或

```
tags: [标签1,标签2,标签3]
```

## 4.1.1.7. categories

定义文章的标签属性 ( Not available for pages )

按如下格式填写即可
```
categories:
    - 分类名
```

## 4.1.1.8. permalink

Overrides the default permalink of the post

## 4.1.1.9. description?

应该还有一个 `description?` 属性，用于写入当前文章的 excerpt（摘要），放在首页，能令首页不显示全文，只显示文章的 description（描述）

注意：要在<a title="\blog\theme\主题名\">主题目录</a>下的`_config.yml`文件，把下方的命令改为“true”，这个功能才能生效。（应该是这样，待测试！）

```
excerpt_description: true
```

## 4.2. 生成静态页面

> 进行这一步操作前建议先使用 `hexo clean` 命令

当文章内容完成编辑以后，同样的回到blog目录下的命令行，执行 `hexo generate` 命令，Hexo便会把source中的内容生成为静态网页内容，存放在public目录下。（此目录就是网站目录）

## 4.3. 在本地建立服务（预览）

只要 public 目录有内容，便可以使用 `hexo server` 命令在本机创建端口号为4000的http访问服务，然后就可以在浏览器通过 http://localhost:4000 访问网站，预览效果。

（一般用于预览成果，没有问题后便可进行后续的部署到远程服务器）

## 4.4. 部署到服务器

> 第一次进行这一步操作前要先在 _config.yml 文件内填写好部署的目标地址信息

当静态网页生成好以后，便可以执行 `hexo deploy` 命令，把public目录下的内容部署到目标地址（可以是私有服务器，或者是Github之类的网站）

# 弃？)))

---
