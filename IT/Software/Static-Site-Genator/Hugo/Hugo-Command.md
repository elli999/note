
<!-- vim-markdown-toc Redcarpet -->

* [hugo](#hugo)
* [hugo --config](#hugo-config)
* [hugo server](#hugo-server)

<!-- vim-markdown-toc -->

<br>

---

## hugo

**Format:** `hugo` 

生成静态网站。即根据md文件及其相关附件、配置等，生成由html页面、CSS文件等组成的静态网站。

> 相当于hexo g命令

--------------------------------------------------------------------------------------------------------

## hugo --config

Hugo uses the config.toml, config.yaml, or config.json (if found in the site root) as the default site config file.

> Hugo 默认会在网站根目录加载网站配置文件，网站配置文件默认是 `config.toml`, `config.yaml`, `config.json`中的其中一个（可根据习惯选择使用，toml、yaml、json的格式不一样）。

The user can choose to override that default with one or more site config files using the command line --config switch.

> 用户可以使用`hugo --config`命令更改网站配置文件的文件名，甚至可以改为加载多个配置文件。

**Examples:**

```
hugo --config debugconfig.toml

hugo --config a.toml,b.toml,c.toml
```

> Multiple site config files can be specified as a comma-separated string to the --config switch.

> 如果在`hugo --config`命令中需要写入多个config files时，可以使用逗号分隔开。


--------------------------------------------------------------------------------------------------------


## hugo server

**Format:** `hugo server` 

启动hugo的本地server，可通过浏览器访问网站，不渲染草稿（draft）文件。

**Parameters**

| Parameter |         Explain          | Example                 | Effect                                                                            |
| :---:     |          :---:           | :---:                   | :---:                                                                             |
| -D        |      渲染draft文件       | hugo server -D          | 启动hugo的本地server，渲染所有文件，包含草稿（draft）文件。                       |
