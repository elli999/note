
<!-- vim-markdown-toc Redcarpet -->

* [showcase](#showcase)
* [FAQ](#faq)
    - [Windows10下出现yarn命令路径或访问权限错误问题](#windows10下出现yarn命令路径或访问权限错误问题)

<!-- vim-markdown-toc -->

<br>

---

## showcase

https://docs.shanyuhai.top/

http://zpj80231.gitee.io/znote/

https://timspan.github.io/


## FAQ

### Windows10下出现yarn命令路径或访问权限错误问题

> 节省时间直接看总结

由于搁置了两个星期没有使用VuePress了，期间还接触了Hugo、Docsify、Gitbook，很多东西印象不深了且混淆了。印象中记得，在Windows10下安装，官方建议先装Nodejs、NPM，然后安装Yarn，再通过yarn安装VuePress。

但是这样安装过后，使用yarn执行VuePress相关命令，会出现报错，报错内容大概意思是说找不到路径（是一条windows常见的路径报错信息）。

> 网上找了很久资料，都没有靠谱的答案，其中一个老外说这个原因是因为Windows下的安装不是通过NVM安装的，但其实我理解他的意思是指Linux和MAC中的NVM，不会出现这种问题。

> 而Github上的Windows版的NVM主页写得很清楚，Windows版不是Linux和Mac版的NVM，是一个毫无关系的、独立的NVM软件（因为写的是英文，这段话是个人理解，但是我认为没有理解错）。推测应该是该名程序员发现没有Windows版是NVM，所以自行独立开发了一个Windows版的。

> 但是后来我使用了NVM依旧出现同样的错误，更加证明当时老外说的只是推测原因，或者说把原因说出来，但是不是说安装Windows版NVM就能解决（毕竟Windows版的NVM和Linux、MAC的毫无关联）

最终我多次测试后，得出可能的原因（不确定，但是能解决），就是yarn的安装路径出现问题。因为yarn安装在`C:\user\用户名\...\Local\...`的目录下，路径过于复杂，而且C盘的目录容易出现访问权限问题。

所以当我把yarn的安装路径改为`D:\yarn\`后，问题就解决了。

**总结：** 鉴于遭遇过这种难搞的问题，我强烈建议，把Nodejs、NPM、yarn、VuePress等，尽量使用自定义安装路径，把路径设置在盘符的根目录下，不要用中文（可以的话大小写也懒得改了），路径更改方法网上有教。期间还遇到过不记得是VuePress还是yarn，要手动在环境变量中添加path的问题。

<br>

---

