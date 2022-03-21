Title: 通过nc命令查看服务器端口和客户端能不能正常连接
Date: 2020-01-08 09:57:04
Category: network
Tags: linux, network
Slug: linux-nc


tcp
```
服务器
nc bind地址 监听端口

客户端
nc 服务器地址 服务器端口
```

udp `nc` 加上 `-u` 参数即可

