Title: 笔记本把无线网络连接分享给网线
Date: 2020-01-07 22:11:18
Category: linux
Tags: linux, network
Slug: laptop-router


笔记本把无线网络连接分享给网线.

首先如果笔记本开了NetworkManager服务, 建议在NetworkManager的配置中取消托管有线网络接口 eth0. (可选, 如果修改了配置, 要重启NetworkManager)

`cat /etc/NetworkManager/NetworkManager.conf`
```txt
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

[keyfile]
unmanaged-devices=interface-name:eth0
```

确定笔记本已经连接好了WIFI

然后在笔记本上面设置 eth0 ip
`sudo ifconfig eth0 192.168.9.1`

开启DHCP
`sudo dnsmasq --dhcp-range=192.168.9.10,192.168.9.20,999m --interface=eth0`

开启转发
`echo 1 > /proc/sys/net/ipv4/ip_forward`

设置NAT
`iptables -t nat -A POSTROUTING -j MASQUERADE`

需要上网的设备连接笔记本eth0即可

查看笔记本下面连接的设备ip
`cat /var/lib/misc/dnsmasq.leases` 或者 `cat /var/db/dnsmasq.leases`

