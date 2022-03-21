Title: 将man page输出到pdf和HTML
Date: 2015-01-20 16:37
Category: linux
Tags: linux
Slug: man-pages-to-pdf

```bash
# 方法1：直接浏览器查看html
man -Hfirefox memfd_create


# 方法2：查询手册页文件位置
man -w timerfd_create  # 或 man -w 2 timerfd_create
# 然后转换为html
zcat /usr/share/man/man2/timerfd_create.2.gz | roff2html > timerfd_create.html


# 方法3：转换为pdf
man -t eventfd | ps2pdf - > eventfd.pdf
```
