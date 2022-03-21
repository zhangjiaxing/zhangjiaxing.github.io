Title: linux开启键盘灯的方法
Date: 2017-06-24 00:13:44
Category: linux
Tags: linux, keyboard, command
Slug: linux-keyboard-led

现在许多背光键盘的背光灯是通过 Scroll 这个键控制的. 
在windows下这没啥问题, 一按 scroll 这个键 ,背光灯就亮了,再按,就灭了.
但是, 在Linux下, 按这个键 scroll 没反应.
所以记录一下linux开启键盘灯的方法

```
# X 中开启键盘灯
xset led on

# X 中关闭键盘灯
xset led off
```
