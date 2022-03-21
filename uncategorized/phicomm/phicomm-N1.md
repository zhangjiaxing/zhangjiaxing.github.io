Title: 斐讯N1刷机过程记录
Date: 2020-07-01 23:38:09
Category: linux
Tags: linux, phicomm
Slug: phicomm-N1

![刷机]({attach}/uncategorized/phicomm/phicomm-N1-flash.jpg)


去年买的N1盒子, 一直没时间折腾, 最近刚好需要作下载机用, 于是刷机, 顺便整理下步骤.


首先说下N1配置. 处理器Amlogic S905, 内存 2G, emmc 8G, 千兆网口, 2个USB 2.0, 1个HDMI接口, 双频WIFI(支持 802.11 ac), 支持蓝牙. 


价格目前不到100元. 和raspberry 4 相比性能差不多, 重要的是能用Android系统, 便宜, 自带外壳.


####目前用的人多的N1系统, 大致为 (不分先后)
- Openwrt做主路由     
- 小钢炮做下载机Docker里做旁路由 (恩山无线论坛 荒野无灯 所开发的专注于下载的系统, 基于linux)
- Armbian玩Docker
- Android (电视盒子)
- 游戏机 (EmuELEC)


##刷机第一步系统降级
不管是N1什么版本，首先必须要降级到能线刷的版本，并且能够使用，便于后期emmc能恢复。

######准备环境
- N1盒子
- 装有windows的电脑主机
- 网线
- HDMI线
- 支持HDMI的电视或者显示器
- USB接口鼠标
- USB2.0公对公数据线

######降级过程
[WEBPAD大神降级教程>>](https://www.right.com.cn/forum/thread-340279-1-1.html)
[超快速恢复EMMC法>>](https://www.right.com.cn/forum/thread-413863-1-1.html)


######设置开启U盘引导, 设置以后, 只要不动bootloader, N1 就刷不死
```
adb connect N1的IP
adb shell reboot update
```


##下面是刷armbian的方法

######下载armbian系统
[当前适配的armbian介绍,下载连接](https://www.right.com.cn/forum/thread-927225-1-1.html)


######烧录进入U盘
linux可以尝试用dd (没测试过)

windows用etcher (亲测可用)

按照上面的说明, 替换 btd文件
```
[/boot/uEnv.ini] 第一行改为
dtb_name=/dtb/meson-gxl-s905d-phicomm-n1.dtb
```

######然后关闭N1, 开始启动armbian
插上U盘,N1通电, 开机就是U盘启动的armbian系统.

也可以通过home目录下面的 install.sh 安装进入emmc. (覆盖掉默认的android)


----------
参考资料 `主要参考 恩山无线论坛 和 什么值得买`

[N1刷不死的玩法整理](https://www.right.com.cn/forum/thread-415880-1-1.html)

[N1刷完ARMBIAN想恢复EMMC超级简单线刷法](https://www.right.com.cn/forum/thread-413863-1-1.html)

[N1玩法总结整理](https://www.right.com.cn/forum/thread-421805-1-1.html)

[N1盒子不拆机救砖](https://post.smzdm.com/p/akmg5dv4/)

[N1改电视盒子](https://post.smzdm.com/p/aekemx44/)

[N1简明降级&刷机教程](https://post.smzdm.com/p/a99vxp9e/)

