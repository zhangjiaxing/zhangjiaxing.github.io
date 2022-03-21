Title: linux设置文件只读, 直到关机
Date: 2017-06-14 09:58:28
Category: linux
Tags: linux, bash, command
Slug: set-file-readonly-until-reboot

```
:::bash
mount -o bind $file $file
mount -o remount,bind,ro $file
```
