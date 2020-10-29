
<!-- vim-markdown-toc Redcarpet -->

* [Rime分类](#rime分类)
* [配置相关](#配置相关)
    - [配置文件结构及路径](#配置文件结构及路径)
    - [修改配置文件时需要注意](#修改配置文件时需要注意)
    - [修改](#修改)
        + [候选词个数](#候选词个数)
* [未分类](#未分类)

<!-- vim-markdown-toc -->

--------------------------------------------------------------------------------------------------------

## Rime分类

* Windows -- 小狼毫
* Linux -- ibus-rime 或 fcitx-rime (可以使用 fcitx、fxitx5、ibus)
* MacOS -- 鼠须管
* Android -- 同文输入法
* IOS -- iRime

## 配置相关

### 配置文件结构及路径

共享资料夹路径

* 【小狼毫】 "安装目录\data"
* 【中州韵】 /usr/share/rime-data/ (EK: Linux?)
* 【鼠须管】 "/Library/Input Methods/Squirrel.app/Contents/SharedSupport/"

用户资料夹路径

* 【小狼毫】 "%APPDATA%\Rime"
* 【中州韵】 ~/.config/ibus/rime/ （0.9.1 以下版本为 ~/.ibus/rime/ ）(EK: Linux?)
* 【鼠须管】 ~/Library/Rime/

**共享资料夹：** 包含预设输入方案的源文件。 这些文件属于 Rime 所发行软件的一部份，在访问权限控制较严格的系统上对用户是只读的，因此谢绝软件版本更新以外的任何修改。一旦用户修改这里的文件，很可能影响后续的软件升级或在升级时丢失数据。

**用户资料夹：** 则包含为用户准备的内容，如：

* 〔全局设定〕 default.yaml
* 〔发行版设定〕 weasel.yaml
* 〔预设输入方案副本〕 <方案标识>.schema.yaml
* ※〔安装信息〕 installation.yaml
* ※〔用户状态信息〕 user.yaml

编译输入方案所产出的二进制文件：

* 〔Rime 棱镜〕 <方案标识>.prism.bin
* 〔Rime 固态词典〕 <词典名>.table.bin
* 〔Rime 反查词典〕 <词典名>.reverse.bin

记录用户写作习惯的文件：

* ※〔用户词典〕 <词典名>.userdb/ 或 <词典名>.userdb.kct
* ※〔用户词典快照〕 <词典名>.userdb.txt、<词典名>.userdb.kct.snapshot 见于同步文件夹

以及用户自己设定的：

* ※〔用户对全局设定的定制信息〕 default.custom.yaml
* ※〔用户对预设输入方案的定制信息〕 <方案标识>.custom.yaml
* ※〔用户自制输入方案〕及配套的词典源文件

注：以上标有 ※ 号的文件，包含用户资料，您在清理文件时要注意备份！

### 修改配置文件时需要注意

严格遵守 yaml 语法，缩进都是两个空格，不能用 tab 代替，否则配置是无效的。

只能有一个`patch:` 行，如有相同的项目请合并。

### 修改

#### 候选词个数

修改用户资料夹的 `default.custom.yaml` ，找到 `menu/page_size` 字段，如果没有则创建，设置该字段的值即可。例如

```
patch:
  "menu/page_size": 8
    schema_list:
        - schema: clover
```

详见 [一例、定制每页候选数](https://github.com/rime/home/wiki/CustomizationGuide#%E4%B8%80%E4%BE%8B%E5%AE%9A%E8%A3%BD%E6%AF%8F%E9%A0%81%E5%80%99%E9%81%B8%E6%95%B8)

--------------------------------------------------------------------------------------------------------


## 未分类

Rime做任何修改，基本上都要使用“重新部署”功能，才能使修改生效。
