Title: openSUSE coredump文件
Date: 2020-08-24 12:40:41
Category: linux
Tags: openSUSE, gdb
Slug: openSUSE-coredump

openSUSE Leap 15.2 默认是不开启coredump的.


######开启方法
1. 查看`ulimit -H -a` 和 `ulimit -S -a` core files是否均显示unlimited. 如果不是则修改
2. sudo zypper in systemd-coredump
3. reboot


######使用方法
1. sudo coredumpctl list 列出当前corefile 文件
2. /var/lib/systemd/coredump/ 这是corefile 默认保存位置
3. man systemd-coredump; man core 查看手册

