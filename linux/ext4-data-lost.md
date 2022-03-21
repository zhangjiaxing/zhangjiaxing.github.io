Title: ext4断电丢失数据(零长文件)
Date: 2019-11-29 21:10:42
Category: linux
Tags: linux, ext4
Slug: ext4-data-lost

ext4断电丢失数据(零长文件).

嵌入式设备, 经常拔掉电源, 以前/data分区有挂载选项 sync.

后来发现sync方式挂载写入数据速度太慢了(100KB/S), 正常为10MB/S.

去掉sync断电又会丢数据.

ext4 man-pages 上说 `fd = open("foo", O_TRUNC)/write(fd,...)/close(fd)` 或者好一点的 `fd = open("foo.new")/write(fd,...)/close(fd)/ rename("foo.new", "foo")` 这种用法突然断电容易产生零长文件, 在close之前调用fsync好一点. 实际上 auto_da_alloc 挂载选项就是为了解决上面的一些情况的, man-pages上说auto_da_alloc 相对及时把数据写进硬盘. 但是自己测试断电依然会丢数据, 产生零长文件(`zero-length`) .

尝试新的挂载选项为 defaults,noatime,nodelalloc,auto_da_alloc,commit=1,data=journal, 不带sync. 不知道管用不管用.


有人推荐xfs, 据说断电不容易丢数据, 但xfs用于读写密集的环境会有一些问题, 读写密集环境用ext4.

