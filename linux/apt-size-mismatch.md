Title: apt install 一直 size mismatch
Date: 2017-6-03 8:32
Category: linux
Tags: debian, linux
Slug: apt-size-mismatch

raspberry pi 的 debian， apt安装软件是一直提示 size mismatch。
后来发现这是运营商(ISP)缓存的问题， 运营商有些时候是通过文件名作为缓存的， 导致服务器文件更新后，用户依然下载到旧的版本。
解决方法是， apt source 使用https协议就好了。

后来发现有人和我遇到同样的问题：https://bbs.deepin.org/forum.php?mod=viewthread&tid=138536
