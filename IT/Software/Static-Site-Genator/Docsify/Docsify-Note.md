
[Docsify Website](https://docsify.js.org/)

[Docsify Documentation](https://elli999.gitee.io/note/#/IT/Software/Static-Site-Genator/Docsify/Documentation/README)

[Docsify Documentation zh](https://docsify.js.org/#/zh-cn/)  for temp

## About Docsify

Docsify is the most easiest Static Site Genator(SSG) I ever met.

**Feature**

* Fast
  * no need to render markdown to html
  * very small, easy to install
  * local server is real-time update
* suit to write Documentation
* official document is easy to understand.(Hugo & VuePress is hard to study)

**Showcase**

[Snailclimb/docsify-demo](https://snailclimb.gitee.io/docsify-demo/#/)
[SnailClimb/JavaGuide-Interview](https://snailclimb.gitee.io/javaguide-interview/)

## Installation

1. Install Nodejs & NPM
2. 


<br>

---

## My Docsify index file

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Description">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/lib/themes/vue.css">
  <link rel="stylesheet" href="sidebar-folder.css" />
</head>
<body>
  <div id="app"></div> <!--you can add text in here, default is "Loading...", you can change to "加载中"-->
  <nav>
    <a href="#/">EN</a>
    <a href="#/IT/">IT</a>
  </nav>
  <script>
    window.$docsify = {
      name: '',
      repo: '',
      homepage: 'README.md',
      //logo: '/_media/ek_favicon.png',
      // coverpage: true,
      loadSidebar: true,
      <!--这一段要学习一下，为什么？-->
      alias: {
        '/.*/_sidebar.md': '/_sidebar.md', 
      },
      subMaxLevel: 3,  // sidebar设置：根据用户设定的标题层级数值，把文章中的标题加入到sidebar里面。例如如果设定值为2，则把 # 和 ## 的标题加入，三级及以后的不加入
      autoHeader: true, // （应该是是默认打开的了，即设置为true没有变化）
      loadNavbar: true,
      auto2top: true,  // 切换页面后是否自动跳转到页面顶部
      name: 'Eason Kong Note', // Website name as it appears in the sidebar.
      noEmoji: true,
      maxLevel: 5,  // 最大支持渲染的标题层级?
      // 全文搜索 plugin
      search: {
        //maxAge: 86400000,  // 过期时间，单位毫秒，默认一天
        paths: 'auto',
        placeholder: 'Type to search',
        noData: 'No Result!',
        // 搜索标题的最大层级，1 - 6
        depth: 2,
        hideOtherSidebarContent: true // 激活搜索框时是否隐藏原有的sidebar内容
      },
      formatUpdated: '{MM}/{DD} {HH}:{mm}',
      pagination: {
        previousText: 'Pre Page',
        nextText: 'Next Page',
        crossChapter: true,
        crossChapterText: true,
      },
    }
  </script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>
  <!--Mermaid-->
  <script src="//unpkg.com/mermaid/dist/mermaid.js"></script>
  <script src="//unpkg.com/docsify-mermaid@latest/dist/docsify-mermaid.js"> 
  <script>mermaid.initialize({ startOnLoad: true });</script>
  <!--Sidebar collapse-->
  <script src="//unpkg.com/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
</body>
</html>
```


## 心得

* sidebar暂时不知道如何设成可展开和收缩的，所以所有文件都会全部显示出来，文章一多就很混乱，十分不美观。但是根据文章里面的标题（即# ## ### ... 的标题二、标题三）自动会在sidebar生成的TOC，则可以点一下展开、再点一下收起。

> 一个可以变美观的想法：就是不要分太多文章，例如Go语言下的所有文章合为一篇，通过标题# ## ###来分章节，这是一个临时办法，但是我不太喜欢，会导致文章很长。

> 最好的办法应该是：sidebar可以展开和收缩，同时TOC是生成在另一个框体中，用户可以打开/关闭，点击跳转。（现在是TOC自动生成结合在sidebar内）
