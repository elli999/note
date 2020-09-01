---
title: "hugo-theme-Learn"
---

<!--

>>> Hidden Directory <<<

[<basics>](./basics/_index)
[<Content>](./cont/_index)
[<shortcodes>](./shortcodes/_index)
[credits.md](./credits)
[showcase.md](./showcase)

-->


EK: The time of this document's download is 2020-08-25.

{{% expand " " %}}这份文档的下载时间是2020.08.25{{% /expand %}}


# Hugo learn theme

[Hugo-theme-learn](http://github.com/matcornic/hugo-theme-learn) is a theme for [Hugo](https://gohugo.io/), a fast and modern static website engine written in Go. Where Hugo is often used for blogs, this multilingual-ready theme is **fully designed for documentation**.

{{% expand " " %}}hugo-theme-learn是一个Hugo主题。Hugo是一个用Go语言开发的快速且现代化的静态网站引擎，常被用于搭建博客。而这款支持多语言的主题learn是**完全为了编写文档**而设计的。{{% /expand %}}

This theme is a partial porting of the [Learn theme](http://learn.getgrav.org/) of [Grav](https://getgrav.org/), a modern flat-file CMS written in PHP.

{{% notice tip %}}Learn theme works with a _page tree structure_ to organize content : All contents are pages, which belong to other pages. [read more about this]({{%relref "cont/pages/_index.md"%}}) 
{{% /notice %}}

## Main features

* [Automatic Search]({{%relref "basics/configuration/_index.md#activate-search" %}})
* [Multilingual mode]({{%relref "cont/i18n/_index.md" %}})
* **Unlimited menu levels**
* **Automatic next/prev buttons to navigate through menu entries**
* [Image resizing, shadow...]({{%relref "cont/markdown.en.md#images" %}})
* [Attachments files]({{%relref "shortcodes/attachments.en.md" %}})
* [List child pages]({{%relref "shortcodes/children/_index.md" %}})
* [Mermaid diagram]({{%relref "shortcodes/mermaid.en.md" %}}) (flowchart, sequence, gantt)
* [Customizable look and feel and themes variants]({{%relref "basics/style-customization/_index.md"%}})
* [Buttons]({{%relref "shortcodes/button.en.md" %}}), [Tip/Note/Info/Warning boxes]({{%relref "shortcodes/notice.en.md" %}}), [Expand]({{%relref "shortcodes/expand.en.md" %}})

![Screenshot](screenshot.png?classes=shadow)

## Contribute to this documentation
Feel free to update this content, just click the **Edit this page** link displayed on top right of each page, and pullrequest it

{{% notice info %}}
Your modification will be deployed automatically when merged.
{{% /notice %}}

## Documentation website
This current documentation has been statically generated with Hugo with a simple command : `hugo -t hugo-theme-learn` -- source code is [available here at GitHub](https://github.com/matcornic/hugo-theme-learn)

{{% notice note %}}
Automatically published and hosted thanks to [Netlify](https://www.netlify.com/). Read more about [Automated HUGO deployments with Netlify](https://www.netlify.com/blog/2015/07/30/hosting-hugo-on-netlifyinsanely-fast-deploys/)
{{% /notice %}}
