Title: inotify-tools
Date: 2020-04-24 19:40:05
Category: linux
Tags: linux, kernel
Slug:  inotify-tools

inotify-tools 可以用来监控文件系统的事件。inotify-tools提供两种工具，一是 inotifywait，它是用来监控文件或目录的变化，二是inotifywatch，它是用来统计文件系统访问的次数。

常用`inotifywait -qcrm $dir`


######inotifywait
```md
参数：
@
排除不需要监视的文件，可以是相对路径，也可以是绝对路径。
–fromfile 
从文件读取需要监视的文件或排除的文件，一个文件一行，排除的文件以@开头。
-m, –monitor
接收到一个事情而不退出，无限期地执行。默认的行为是接收到一个事情后立即退出。
-d, –daemon
跟–monitor一样，除了是在后台运行，需要指定–outfile把事情输出到一个文件。也意味着使用了–syslog。
-o, –outfile 
输出事情到一个文件而不是标准输出。
-s, –syslog
输出错误信息到系统日志
-r, –recursive
监视一个目录下的所有子目录。
-q, –quiet
指定一次，不会输出详细信息，指定二次，除了致命错误，不会输出任何信息。
–exclude 
正则匹配需要排除的文件，大小写敏感。
–excludei 
正则匹配需要排除的文件，忽略大小写。
-t , –timeout 
设置超时时间，如果为0，则无限期地执行下去。
-e , –event 
指定监视的事件。
-c, –csv
输出csv格式。
```

######inotifywatch
```md
参数：
@
排除不需要监视的文件，可以是相对路径，也可以是绝对路径。
–fromfile 
从文件读取需要监视的文件或排除的文件，一个文件一行，排除的文件以@开头。
-z, –zero
输出表格的行和列，即使元素为空
–exclude 
正则匹配需要排除的文件，大小写敏感。
–excludei 
正则匹配需要排除的文件，忽略大小写。
-r, –recursive
监视一个目录下的所有子目录。
-t , –timeout 
设置超时时间
-e , –event 
只监听指定的事件。
```
