
[TheCW视频](https://www.bilibili.com/video/BV11J411a7Tp)

03:00 介绍屏幕

05:00 进入Arch命令行，开始安装前的设置工作

07:30 简单配置Vim

??:?? 配置网络

12:30 配置时间


---

一定要看官方文档

改字体 `setfont /usr/share/kbd/consolefonts/LatGrkCyr-12x22.psfu.gz` 

改键盘布局 `loadkeys colemak` 

---

`vim keys.conf`

```Vim
" 把Esc键改为CapsLock键
keycode 1 = Caps_Lock 

" 把CapsLock键改为Esc键
keycode 58 = Escape
```

`loadkeys keys.conf`

---

`vim .vimrc`

---

装Arch过程要连网

查看当前网络设备 `ip link`

一般情况下，看到`wlan0`是指无线网卡（应该`lo`是有线网卡）

下面以设置wlan0为例，`ip link set wlan0 up` 为打开无线网卡

这个时候，再次输入`ip link`可以看到，`wlan0`从原来的

```
wlan0: <BROADCAST,MULTICAST> ...
```

变为

```
wlan0: <No-CARRIER,BROADCAST,MULTICAST,UP> ...
```

关键是这个`UP`，代表wlan0已经打开了。

接下来，使用`iwilst wlan0 scan`扫描当前电脑能接收到的附近的wifi信号并列出 

扫描完后，发现输出的信息有点多。

> `CTRL L` 是清屏，或者使用`clear`命令

重新使用`iwilst wlan0 scan | grep ESSID`命令进行扫描。

现在可以清晰看到附近所有的wifi热点了。

`wpa_passphrase Wifi名 用户名 密码 > internet.conf`

`vim internet.conf` 核对信息无误后可以退出。

`wpa_supplicant -c internet.conf -i wlan0 &`

> `-i 设备名` 这里的i是用于指定设备
> `&` 加了这个让这个命令在后台运行
 
这个时候，`ping baidu.com`会发现没有网

因为没有配置IP，可以使用Arch自带的动态分配IP地址的工具dhcpcd。

`dhcpcd &`

成功后再ping一次，发现网络连上了。

---

## 配置时间
