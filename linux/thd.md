Title: 树莓派中开机时检测案件是否按下
Date: 2021-08-01 15:16:55
Category: linux
Tags: linux, raspberry
Slug: thd


```bash
# 记录一下此用法。 thd来自 debian 软件包 triggerhappy
if [ -x /usr/sbin/thd ] && timeout 1 thd --dump /dev/input/event* | grep -q "LEFTSHIFT\|RIGHTSHIFT"; then
      printf "xxxxxxxx" 
fi
```
