Title: uart登录显示颜色支持分屏
Date: 2021-08-17 18:25:03
Category: linux
Tags: linux
Slug: uart-tty


使用minicom登录的时候，远程终端窗口大小和本地窗口不一致。 远程窗口小不好用。

经测试可以用 `sudo screen /dev/ttyUSB0 115200` 来登录， 登录后使用`stty`修改tty大小。可根据本机终端模拟器默认设置修改。


`stty size` 查看当前tty大小

`stty rows 52 cols 191` 修改tty大小

----
#### 显示颜色

由于minicom不支持带颜色的终端类型， 所以可以用screen登录 `sudo screen /dev/ttyUSB0 115200 -T linux`

在树莓派上执行：
```bash
echo >> /root/.profile
echo '[[ "$(tty)" == /dev/ttyS0 ]] && stty rows 55 cols 190 && TERM=linux bash && exit'  >> /root/.profile
```

同时解决uart登录显示颜色和终端大小问题, 这样就可以用tmux分屏了


