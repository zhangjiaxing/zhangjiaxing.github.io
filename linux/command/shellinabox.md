Title: shellinabox
Date: 2018-05-22 19:37:34
Category: linux
Tags: shell, terminal, web, linux
Slug: shellinabox


shellinabox 能够通过Web浏览器模拟一个远程系统的Shell. 它和SSH没有任何关系.

shellinaboxd -t  (开启一个login shell)

shellinaboxd -t -s '/:root:root:/:/bin/bash' --port=8080  (不需要输入密码,直接登陆)
