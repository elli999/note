---
title: Windows-日常使用
date: 2020-07-28 19:15:38
tags:
    - Windows
    - OS
categories:
    - [+IT, OS, Windows]
---

> Windows系统的所有日常使用技巧汇总


<!-- vim-markdown-toc Redcarpet -->

* [---](#)
* [在终端打开当前目录的GUI资源管理器](#在终端打开当前目录的gui资源管理器)
* [更改键盘按键映射](#更改键盘按键映射)
	- [系统法](#系统法)
	- [两键互换](#两键互换)
	- [屏蔽按键示例](#屏蔽按键示例)
	- [还原修改](#还原修改)
	- [特别说明](#特别说明)
	- [附表：《键盘扫描码表》](#附表：《键盘扫描码表》)
	- [我的配置](#我的配置)
	- [参考](#参考)
* [---](#)
* [鼠标键功能](#鼠标键功能)
* [---](#)

<!-- vim-markdown-toc -->

<!-- more -->


---
---


## 在终端打开当前目录的GUI资源管理器

* Windows10

```
explorer .
```

## 更改键盘按键映射

> 通过对键盘进行更改按键映射的操作，实现在windows和linux中，按A键输出B，或者屏蔽某个按键的功能。

* 软件法

就是下载改键软件，网上搜索有很多，有条件的可以使用autohotkey自行编写

缺点：软件要常驻后台，占用少量内存。

优点：灵活方便，不用的时候可以关掉。

* 系统法

通过`更改注册表(windows)`实现，下面以本方法展开讲解。

---

### 系统法

本方法适用系统：Windows XP、Windows 2000、Windows 10

**示例**

**1. 打开记事本，并粘贴下面模板内容**
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,5c,e0,38,e0,00,00,00,00
```
**2. 按保存，并命名为 `*.reg` （ `*` 号代表任意文件名）**

**3. 内容讲解**

```
hex:00,00,00,00,00,00,00,00,02,00,00,00,5c,e0,38,e0,00,00,00,00
```

可以看成是

```
hex:00,00,00,00,00,00,00,00,02,00,00,00,AA,AA,BB,BB,00,00,00,00
```

为了方便讲解，再进行一次排版

```
00,00,00,00,00,00,00,00,
02,00,00,00,
AA,AA,BB,BB,
00,00,00,00
```

含义为：
```
| 版本号和头部字节 |
| 映射更改组数 |
| 第一组 | 第二组 | 第三组 | 第四组 | 如此类推 ...
| 结尾终止 | 
```
* 第一行

不用改，填 `00,00,00,00,00,00,00,00,` （即16个0，共8组）

* 第二行

根据后面你要改的键数，把键数+1后填写，如 `02,00,00,00,` 代表改一个键。（因为要加上第四行的4组0，所以要 `键数+1` 后填写）

* 第三行

`AA,AA,BB,BB`，`AA,AA`是按键A的扫描码，`BB,BB`是按键B的扫描码，码表在后面，根据需求自行查询填写。

`AA,AA,BB,BB` 连起来就是把按键A的功能放在按键B的位置，即按B键，实际输出A键（用A替代B，B就没有了）。

> 注意：在注册表中输入时，需要将扫描码的高低字节交换一下。即如果查到的按键扫描码是`12,34`，需要把它调整为`34,12`

如果要改动多组映射，则在此行继续添加即可。

示例 `AA,AA,BB,BB,CC,CC,DD,DD,EE,EE,FF,FF, ...` 如此类推。


* 第四行

最后固定以 `00,00,00,00` 结尾。

**4. 根据需求填写完毕后，按原格式排版并保存、运行、重启，即可生效**

> 改回原格式，四行只是为了方便讲解

原格式示例

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,5c,e0,38,e0,00,00,00,00
```

这里的`5c,e0`是Right Windows键，`38,e0`是Right Alt键，所以这个示例是把键盘中的右Alt键更改成右win键了。

### 两键互换

如果要两键互换位置的话，要写两组

`AA,AA,BB,BB` 只是把A键放到B键的位置中去，B键相当于没有了

要两键互换，要这样写

```
AA,AA,BB,BB,BB,BB,AA,AA,
```

### 屏蔽按键示例

如果想要某个键失效，在更改后的扫描码中填写`00,00`即可。

**示例**

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,00,00,38,e0,00,00,00,00
```

> （未测试，应该是这样）

主要看的是`02,00,00,00`后面的`00,00,38,e0`，意思是用`00,00`（空键）写入到`38,e0`的键盘位置中，即`38,e0`这个按键被屏蔽、无效了。


### 还原修改 

即撤销修改

若要恢复键盘键位原来的布局，只需在`开始`-`运行`-`输入regedit后回车`（打开注册表），然后进入`[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]`路径中，找到并删除`Scancode Map`键值，重启即可。


### 特别说明

* 在目前的Windows版本下面，对键盘映射是全局的，而不是针对某个用户的，如果您修改添加或者删除了某个映射，那么不管哪个用户使用，键盘都发生了变化；
* 如果一台电脑有多个键盘，那这些键盘都会产生同样的变化。
* 在XP上不能屏蔽 POWER SLEEP WAKE UP 这三个键。（没有亲自测试，笔记本上没有这三个键
* ThinkPad 上的 Fn 键是不能被映射的，因为它不能被OS识别，所以不能使用上面的方式进行设置。thinkpad新版的bios里面提供了一个功能，让左侧的“Fn”键和相邻的“Ctrl”键进行功能互换。（如果在笔记本的 bios上找不到这个功能的话，需要刷新版bios）
* 导入或设置或修改或删除注册表键值后，重启你的电脑，改变就生效了。

### 附表：《键盘扫描码表》

```
Backspace       00 0E
Caps Lock       00 3A
Delete          E0 53
End             E0 4F
Enter           00 1C
Escape          00 01
HOME            E0 47
Insert          E0 52
Left Alt        00 38
Left Ctrl       00 1D
Left Shift      00 2A
Left Windows    E0 5B
Num Lock        00 45
Page Down       E0 51
Page Up         E0 49
Power           E0 5E
PrtSc           E0 37
Right Alt       E0 38
Right Ctrl      E0 1D
Right Shift     00 36
Right Windows   E0 5C
Scroll Lock     00 46
Sleep           E0 5F
Space           00 39
Tab             00 0F
Wake            E0 63
0               00 52
1               00 4F
2               00 50
3               00 51
4               00 4B
5               00 4C
6               00 4D
7               00 47
8               00 48
9               00 49
-               00 4A
*               00 37
.               00 53
/               00 35
+               00 4E
Enter           E0 1C
F1              00 3B
F2              00 3C
F3              00 3D
F4              00 3E
F5              00 3F
F6              00 40
F7              00 41
F8              00 42
F9              00 43
F10             00 44
F11             00 57
F12             00 58
F13             00 64
F14             00 65
F15             00 66
Down            E0 50
Left            E0 4B
Right           E0 4D
Up              E0 48
Calculator      E0 21
E-Mail          E0 6C
Media Select    E0 6D
Messenger       E0 11
My Computer     E0 6B
' "             00 28
- _             00 0C
, <             00 33
. >             00 34
/ ?             00 35
; :             00 27
[ {             00 1A
\ |             00 2B
] }             00 1B
` ~             00 29
= +             00 0D
0 )             00 0B
1 !             00 02
2 @             00 03
3 #             00 04
4 $             00 05
5 %             00 06
6 ^             00 07
7 &             00 08
8 *             00 09
9 (             00 0A
A               00 1E
B               00 30
C               00 2E
D               00 20
E               00 12
F               00 21
G               00 22
H               00 23
I               00 17
J               00 24
K               00 25
L               00 26
M               00 32
N               00 31
O               00 18
P               00 19
Q               00 10
R               00 13
S               00 1F
T               00 14
U               00 16
V               00 2F
W               00 11
X               00 2D
Y               00 15
Z               00 2C
Close           E0 40
Fwd             E0 42
Help            E0 3B
New             E0 3E
Office Home     E0 3C
Open            E0 3F
Print           E0 58
Redo            E0 07
Reply           E0 41
Save            E0 57
Send            E0 43
Spell           E0 23
Task Pane       E0 3D
Undo            E0 08
Mute            E0 20
Next Track      E0 19
Play/Pause      E0 22
Prev Track      E0 10
Stop            E0 24
Volume Down     E0 2E
Volume Up       E0 30
? -             00 7D
              E0 45
Next to Enter   E0 2B
Next to L-Shift E0 56
Next to R-Shift E0 73
DBE_KATAKANA    E0 70
DBE_SBCSCHAR    E0 77
CONVERT         E0 79
NONCONVERT      E0 7B
Internet        E0 01
iTouch          E0 13
Shopping        E0 04
Webcam          E0 12
Back            E0 6A
Favorites       E0 66
Forward         E0 69
HOME            E0 32
Refresh         E0 67
Search          E0 65
Stop            E0 68
My Pictures     E0 64
My Music        E0 3C
Mute            E0 20
Play/Pause      E0 22
Stop            E0 24
+ (Volume up)   E0 30
- (Volume down) E0 2E
|<< (Previous) E0 10
>>| (Next)      E0 19
Media           E0 6D
Mail            E0 6C
Web/Home        E0 32
Messenger       E0 05
Calculator      E0 21
Log Off         E0 16
Sleep           E0 5F
Help(on F1 key) E0 3B
Undo(on F2 key) E0 08
Redo(on F3 key) E0 07
Fwd (on F8 key) E0 42
Send(on F9 key) E0 43

```

### 我的配置

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,04,00,00,00,5c,e0,38,e0,3a,00,01,00,01,00,3a,00,00,00,00,00
```

方便观看版：
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:
00,00,00,00,00,00,00,00,
04,00,00,00,
5c,e0,38,e0,
3a,00,01,00,
01,00,3a,00,
00,00,00,00
```


* 我把 `右alt` 改成 `右win` 键（因为我有一个 `IBM 8845键` ，这个键盘没有win键，不太方便。)
* 我把 `Caps Lock` 和 `ESC` 键进行了互换（当时是为了方便使用Vim，但最后又取消了这项更改，因为可以直接在`vimrc`文件中更改按键，没必要全系统都改变）


### 参考

- [《修改键盘键位的布局》 by 火の龍果](https://chengchaos.github.io/2019/06/18/windows-scancode-map.html)
- [《修改windows的注册表以实现修改键盘按键的映射》 ](https://blog.csdn.net/u010695008/article/details/51752278)
- [《通过注册表修改键盘按键的映射》 ](http://blog.chinaunix.net/uid-174325-id-3912617.html)



---
---



## 鼠标键功能

`ALT SHIFT NumLock` 开关鼠标键功能（总开关）

> 需要先打开鼠标键功能，下列按键才能生效

---

`NumLock` 临时开关

---

**移动键**

`8` 上移

`2` 下移

`4` 左移

`6` 右移

---

**改变操作键**

`/` 改变操作键为：左键

`*` 改变操作键为：左右同时按键

`-` 改变操作键为：右键

---

**操作键**
 
`5` 单击

`+` 双击

`0` 按住（拖拽）

`.` 松开

---
---
