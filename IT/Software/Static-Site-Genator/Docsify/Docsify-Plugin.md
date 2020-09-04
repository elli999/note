
<!-- vim-markdown-toc Redcarpet -->

* [Sidebar Collapse](#sidebar-collapse)
* [Mermaid](#mermaid)

<!-- vim-markdown-toc -->

## Sidebar Collapse

[https://github.com/iPeng6/docsify-sidebar-collapse](https://github.com/iPeng6/docsify-sidebar-collapse)

first of all, you need to add these in `index.html`

```
<script>
  window.$docsify = {
    loadSidebar: true,
    alias: {
      '/.*/_sidebar.md': '/_sidebar.md',
    },
    subMaxLevel: 3,
    ...
  }
</script>

<!-- Docsify had provide this line, don't add it repeatdly -->
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>

<!-- plugins -->
<script src="//unpkg.com/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
```

Then, this plugin have two Style(CSS):

* [arrow style](https://github.com/iPeng6/docsify-sidebar-collapse/blob/master/src/sidebar.css)
* [folder style](https://github.com/iPeng6/docsify-sidebar-collapse/blob/master/src/sidebar-folder.css)

you can save these two style css file in the Docsify root path, for example the `folder style` CSS file name: sidebar-folder.css. Then edit the `index.html`, add this line `<link rel="stylesheet" href="sidebar-folder.css" />` into the `<head>` section.

## Mermaid

[https://github.com/Leward/mermaid-docsify](https://github.com/Leward/mermaid-docsify)

Add these in the `index.html` file:

```
<script src="//unpkg.com/mermaid/dist/mermaid.js"></script>
<script src="//unpkg.com/docsify-mermaid@latest/dist/docsify-mermaid.js"> 
<script>mermaid.initialize({ startOnLoad: true });</script>
```

now you can include mermaid diagrams in your docsify docs.
