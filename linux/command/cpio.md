Title: cpio
Date: 2017-08-20 12:31:36
Category: linux
Tags: linux, command
Slug: linux-cpio


* 建立 cpio文件 
```
find ./files | cpio -o -H newc > filename.cpio
```

* 解开cpio文件
```
cd  dir1
cpio -ivd  < filename.cpio  
```

* 查看cpio文件中的内容
```
cpio -ivt < filename.cpio
```

`* 如果find显示文件路径是绝对的， 那么解压后可能会覆盖已有文件。 最好使用相对路径压缩。`

