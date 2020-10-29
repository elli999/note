
<!-- Docsify/note/IT/Software/Node/PM2 -->


<!-- vim-markdown-toc Redcarpet -->

* [Definition](#definition)
* [Installation](#installation)
* [Command](#command)
    - [start](#start)
    - [stop](#stop)
    - [restart](#restart)
    - [reload](#reload)
    - [delete](#delete)
    - [list,ls,status](#list-ls-status)
    - [logs](#logs)
    - [monit](#monit)
    - [plus](#plus)
    - [update](#update)

<!-- vim-markdown-toc -->

## Definition

PM2: Advanced, production process manager for Node.JS.

PM2 is a daemon process manager that will help you manage and keep your application online 24/7.

Website: https://pm2.keymetrics.io/

Documentation: https://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/

## Installation

```
npm install -g pm2
```

or

```
$ npm install pm2@latest -g
# or
$ yarn global add pm2
```

## Command

### start

pm2 can start file type: js, sh, py, binary-file ... and so on.

```
pm2 start app_name
```

### stop

```
pm2 stop app_name
```

### restart

```
pm2 restart app_name
```

### reload

EK: what is "reload" use for?

```
pm2 reload app_name
```

### delete

When a PM2 procress started, it will always stay in PM2 list. no matter stop or crash. If you don't need it anymore, you should delete it.

```
pm2 delete app_name
```

### list,ls,status

```
pm2 [list|ls|status]
```

list, ls, status is the same

### logs

```
pm2 logs
```

To dig in older logs:

```
pm2 logs --lines 200
```

### monit

all progress monitor

```
pm2 monit
```

### plus

Web based dashboard, cross servers with diagnostic system:

> Need account?

```
pm2 plus
```

### update

```
pm2 update
```


