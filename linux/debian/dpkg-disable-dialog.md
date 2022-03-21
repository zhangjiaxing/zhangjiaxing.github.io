Title: dpkg安装软件包禁用dialog对话框
Date: 2020-08-14 17:38:05
Category: linux
Tags: linux, debian
Slug: dpkg-disable-dialog

之前写了个脚本, 在后台自动安装某些dpkg软件包.  但是安装过程会卡住 (即使crontab运行的后台程序也会卡住). 分析原因发现是因为后台出了dialog的对话框, 没有被选择导致一直卡住.

于是想到在非tty下面, dialog应该不会出现了. 

首先测试 `yes | dpkg -i *` 对话框还是会出现. (`yes | dpkg -i` 印象里面看别人这么写过.  `yes | tty` 显示 `not a tty`)

于是测试 ssh -T 链接本机, 安装果然没有对话框. 能够成功安装,但是有一行报错 `debconf: unable to initialize frontend: Dialog`

顺着这个报错, 终于搜到了 如何dpkg安装软件不出现dialog对话框.

```
设置环境变量, 然后在 dpkg安装就可以
DEBIAN_FRONTEND=noninteractive dpkg -i *
```
