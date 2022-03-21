Title: pelican博客搭建总结
Date: 2017-6-03 6:56
Category: blog
Tags: pelican, python, blog
Slug: pelican

#### pelican介绍
[Pelican][pelican] 是用Python实现的一个静态网站生成器. 支持以下功能：

* 使用 Markdown 或 reStructuredText 或 AsciiDoc 来编写内容
* 生成静态网页
* 支持许多主题与插件
* 语法高亮
* 支持从很多地方导入

#### 使用方法
参考 https://getpelican.com/ 和 http://docs.getpelican.com/en/stable/

#### windows遇到的一些坑
* windows 平台下 `ValueError: embedded null byte` 的报错
解决方法：
在 `.\lib\site-packages\pelican\utils.py` 文件中， 找到函数 `strftime` ，在第一行添加 `locale.setlocale(locale.LC_ALL, 'en')`
参考 [stackoverflow中的解决方法][stackoverflow]
* windows 平台下 `ghp-import` 应该安装pip中的最新版， 并非 pelican3.7.1文档 所说的 `https://github.com/chevah/ghp-import/archive/win-support.zip`

#### 参考连接：
* [pelican官方网站][pelican]
* [pelican文档][pelicandoc]
* [stackoverflow: How to fix Pelican error][stackoverflow]
* [Chinese version: How to fix Pelican error][fixErrorCN]

[pelican]: <https://getpelican.com/> (pelican)
[pelicandoc]: <http://docs.getpelican.com/en/stable/> (pelican文档)
[stackoverflow]: <https://stackoverflow.com/questions/34434190/value-error-embedded-null-byte-when-using-pelican-content-command-to-generate-m> (stackoverflow)
[fixErrorCN]: <http://xingjian.me/how-to-fix-value-error-embedded-null-byte-error.html> (How to fix Python error: ValueError: embedded null byte)

