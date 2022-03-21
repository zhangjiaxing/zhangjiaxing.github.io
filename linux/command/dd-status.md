Title: dd / 复制 文件显示进度
Date: 2017-08-13 22:00:20
Category: linux
Tags: linux, command
Slug: dd-status

#### dd
1. dd 使用参数 `status=progress`
2. `killall / pkill -USR1 dd`
3. 使用pv命令. `pv src > dest`

#### 复制文件
1. rsync -a --progress src dest
2. scp -v #在不同机器上拷贝显示进度条

