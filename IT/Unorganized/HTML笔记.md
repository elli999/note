---
title: HTML笔记
date: 2020-06-18 22:51:57
tags:
	- HTML
	- 前端
categories:
	- [+IT, Coding, HTML]
---

# 标签查询

## img

`img` means image

一般格式
```
<img src="test.png" alt="Image" width:100% height:100%> 
```

<!-- more -->

### 改变图像大小

**按像素**
```html
<img src="test.png" alt="Image" width:100px height:100px> 
<img src="test.png" alt="Image" style="width:50px;height:50px;" />
```

**按比例**
```html
<img src="bili.png" alt="Image" style="zoom:70%;" />
<img src="bili.png" alt="Image" style="width:80%;height:80%;" />
<img src="pangeru.png" alt="Image" style="transform:scale(0.9)" />
```
第一行的方法好像不行？（待测试！）
第三行的0.9即90%的意思。

---

## mark

mark标签，作用是高亮标签中的内容

```html
<mark>内容</mark>
```

```html
<p>Do not forget to buy <mark>milk</mark> today.</p>
```

输出：

![mark](mark.png)



---

# 名词(属性?)查询

## alt

`alt` means alternate，“替代（文本）”

当设置了alt属性的元素无法加载显示时，会在html页面留下一个对应大小的空间，里面显示着alt的内容。

**示例：**
```
<img src="test.png" alt="上海鲜花港 - 郁金香"  />
```

<div align="center"><img src="test.png" alt="上海鲜花港 - 郁金香"  /></div>
