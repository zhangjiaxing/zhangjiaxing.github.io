Title: 在chromebook上安装archlinux
Date: 2020-7-26 22:56
Category: linux
Tags: archlinux, linux
Slug: arch-linux-samsung-arm-chromebook


1. 把安装到U盘的教程中的 /dev/sda 替换成 mmcblk0 即可把archlinux安装进入系统盘.

2. 编辑 /etc/pacman.conf 文件, 添加 `IgnorePkg   = linux-armv7 linux-armv7-chromebook linux-firmware`

3. 参考https://calvin.me/arch-linux-samsung-arm-chromebook 修改亮度控制 绑定按键 取消静音 设置休眠

```
alsamixer

Go across the page (arrow keys) and press M to unmute
    Left Speaker Mixer Left DAC1
    Left Speaker Mixer Mono DAC2
    Left Speaker Mixer Mono DAC3
    Left Speaker Mixer Right DAC1
    Right Speaker Mixer Left DAC1
    Right Speaker Mixer Mono DAC2
    Right Speaker Mixer Mono DAC3
    Right Speaker Mixer Right DAC1
```


```
cat /usr/local/bin/brightness

#!/bin/bash
cur_bri=$(/usr/bin/cat /sys/class/backlight/backlight.12/brightness)

if [ $1 == "up" ] ; then
    bri=$(($cur_bri+200))
    `echo $bri > /sys/class/backlight/backlight.12/brightness`
fi

if [ $1 == "down" ] ; then
    bri=$(($cur_bri-200))
    `echo $bri > /sys/class/backlight/backlight.12/brightness`
fi

if [ $1 == "-s" ]; then
    `echo $2 > /sys/class/backlight/backlight.12/brightness`
fi
```

Other Notes
```
* The trackpad sometimes doesn't work on boot. A restart fixes it (press the power button)
* Can't seem to get PulseAudio working
* Two finger clicks that are too wide apart don't register as a right click. Two finger taps do though
* Current RAM usage for me is 123M, A LOT better than Chrome OS which always sits around 1.5GB
* Still can't get 720p video to run smoothly. Chrome OS is a bit better here but even then it dies on a 720p60 video. Sticking to 480p seems to be the best thing to do
* It is possible to get rid having to press CTRL + D on each boot, I did that once and totally forgot how to get it back. I eventually did but it was crazy stuff.
```


参考
[archlinuxarm](https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook)
[Arch Linux on Samsung ARM Chromebook](https://calvin.me/arch-linux-samsung-arm-chromebook)
[Chromebook安装ArchLinux](https://www.cnblogs.com/ouyangsong/p/9348163.html)

