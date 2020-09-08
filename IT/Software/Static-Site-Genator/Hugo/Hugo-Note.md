
<!-- vim-markdown-toc Redcarpet -->

* [Showcase](#showcase)
* [Q&A](#q-amp-a)
* [Concept](#concept)
    - [Chapter Page & List page](#chapter-page-amp-list-page)
    - [Content page & Default page & Single page](#content-page-amp-default-page-amp-single-page)
* [Usage](#usage)
    - [创建第一个chapter page：（learn主题教的）](#创建第一个chapter-page：（learn主题教的）)
    - [draft: true](#draft-true)

<!-- vim-markdown-toc -->

<br>

---

## Showcase

https://themes.gohugo.io/hugo-theme-learn/

## Q&A

**Q: 按chapter来分书？**

A: 暂时没有继续学习Hugo了，印象中记得Hugo搭learn主题时，页面结构和Docsify很像，之后重新学习时可参考Docsify看看（说不清楚，看Docsify的源文件目录结构和文件间的跳转方式就明白了）。

**Q: 见下方代码**

```Markdown
### Chapter 1

# Basics
```

A: 这个内容是官方提供的章节首页页面模板内容，推断应该只是作为标题显示的作用，改动应该不会造成结构影响。

<br>

---

## Concept

### Chapter Page & List page

这两个应该是同一种东西，只是叫法不同。

创建chapter page：（learn主题教的）

```
hugo new --kind chapter basics/_index.md
```

> 重点是这里面的`chapter`，这样生成的page就是`chapter page`。

这里的basics是生成后页面的title（EK: 用Docsify结构去思考，其实应该是一样的，只是Docsify的文档建议创建的文档是README.md，其实改为其它名字也可以）

> 按照Hugo相关资料的说法： 一本书只有一个层级（最上级）的才能叫“章节”，不存在“章节”下面的“章节”。

### Content page & Default page & Single page

这三个应该是同一种东西，只是叫法不同。一般是用于放在`Chapter`里面的page。

EK：理解成Chapter是封面，content page是里面的内容页，记载着大量文字的ma？

创建content page：

**two ways**

```
hugo new basic/first-content.md
hugo new basic/second-content/_index.md
```

要学会区分`chapter page`和`content page`

> EK：（其实学会Docsify之后，我觉得不用区分那么多概念性的东西，我觉得只要知道什么样的页面，会出现在什么地方就行。但是还是要看下去Hugo后面怎么说才知道，是不是真的要这么严格区分。）同样地，我觉得不会太纠结概念和区分，按照这两个概念的意思，chapter应该是文档目录的**最高一级的目录的_index.md**使用，其他在最高级的文档，或者是子目录的文档，应该可以统一理解为`content page`。

<br>

---

## Usage

### 创建第一个chapter page：（learn主题教的）

```
hugo new --kind chapter basics/_index.md
```

> 重点是这里面的`chapter`，这样生成的page就是`chapter page`。

这里的basics是生成后页面的title（EK: 用Docsify结构去思考，其实应该是一样的，只是Docsify的文档建议创建的文档是README.md，其实改为其它名字也可以）

> 按照Hugo相关资料的说法： 一本书只有一个层级（最上级）的才能叫“章节”，不存在“章节”下面的“章节”。

要学会区分`chapter page`和`content page`（EK：其实学会Docsify之后，我觉得不用区分那么多概念性的东西，我觉得只要知道什么样的页面，会出现在什么地方就行。但是还是要看下去Hugo后面怎么说才知道，是不是真的要这么严格区分。）

### draft: true

Hugo会在使用命令创建文档时，自动在文档中加上`draft: true`一行在`front matter`中，代表这个页面是“草稿”状态，等你编辑好之后再把这行删除掉，或者改为`draft: false`，Hugo才会在部署时把这篇文章渲染成HTML，否则不会渲染。
