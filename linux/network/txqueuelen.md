Title: linux 设置网络接口发送队列长度
Date: 2021-07-31 01:54:28
Category: network
Tags: linux, network
Slug: txqueuelen

#### 发送队列长度

UDP发送频率过高可能会导致丢包，设置发送队列长度可以解决这类问题。
`https://www.cnblogs.com/liaokang/p/6003334.html`



查询发送队列长度
`ip link show eth0 查看qlen后面的数字`


设置发送队列长度
```bash
# 修改udev配置文件 "/etc/udev/rules.d/70-persistent-net.rules":
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0C:29:35:79:97", KERNEL=="eth*", NAME="eth0", ATTR{tx_queue_len}="10000"
# 或者
ifconfig eth0 txqueuelen 10000
ip link set dev eth0 txqueuelen 10000
```

相关API
```
man 7 netdevice
IOCTLS
SIOCGIFTXQLEN SIOCSIFTXQLEN
```

----
#### 多队列网卡
多队列网卡是一种技术，最初是用来解决网络IO QoS （quality of service）问题的，后来随着网络IO的带宽的不断提升，单核CPU不能完全处满足网卡的需求，通过多队列网卡驱动的支持，将各个队列通过中断绑定到不同的核上，以满足网卡的需求。

查询网卡多队列支持情况
`ethtool -l eth0 | grep combined`

设置网卡队列数
`ethtool -L eth0 combined 2`

