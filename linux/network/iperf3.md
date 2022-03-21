Title: iperf3测试带宽
Date: 2017-6-07 00:00
Category: network
Tags: linux, network
Slug: iperf3


#TCP
服务端`iperf3 -s -p 12345`

客户端测试上传到服务器`iperf3 -c server_host -p 12345`

客户端测试从服务器下载`iperf3 -c server_host -p 12345 -R`


#UDP
客户端添加 -u 参数即可


#传输多个流测试(必加参数)
加上参数 -P 10 (10个流同步测试)


