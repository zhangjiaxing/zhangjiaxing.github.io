Title: iproute2
Date: 2021-8-16
Category: network
Tags: linux, network
Slug: iproute2

## macvlan

`ip link add link eth0 name macvlan0 type macvlan mode bridge`

`ip link delete macvlan0`

1. 实测必须在eth0 up的情况下， macvlan才工作
2. 实测debian 10 (buster)，macvlan下 dhcpcd 8.1.2不能正常工作， isc-dhclient-4.4.1 可以正常工作。 

4种mode

```
根据 macvlan 子接口之间的通信模式，macvlan 有四种网络模式：
    private 模式
    vepa(virtual ethernet port aggregator) 模式
    bridge 模式
    passthru 模式
默认使用的是 vepa 模式。

private
这种模式下，同一主接口下的子接口之间彼此隔离，不能通信。即使从外部的物理交换机导流，也会被无情地丢掉。

vepa
这种模式下，子接口之间的通信流量需要导到外部支持 802.1Qbg/VPEA 功能的交换机上（可以是物理的或者虚拟的），经由外部交换机转发，再绕回来。

注：802.1Qbg/VPEA 功能简单说就是交换机要支持 发夹（hairpin） 功能，也就是数据包从一个接口上收上来之后还能再扔回去。

bridge
这种模式下，模拟的是 Linux bridge 的功能，但比 bridge 要好的一点是每个接口的 MAC 地址是已知的，不用学习。所以，这种模式下，子接口之间就是直接可以通信的。

passthru
这种模式，只允许单个子接口连接主接口，且必须设置成混杂模式，一般用于子接口桥接和创建 VLAN 子接口的场景。
```



## network namespace

```bash
ip netns list  #  显示所有network ns
ip netns add NAME  # 添加network ns
ip netns delete NAME  # 删除network ns
ip link set eth0 netns { PID | NAME }  # 将eth0添加进制定的ns
ip netns exec [NAME] cmd ...  #在ns中执行命令
```



```bash
# 例, 将macvlan0 添加进userns0, 并且查看ip：
ip ns add userns0
ip link set macvlan0 netns userns0
ip netns exec ip addr show macvlan0
ip link set macvlan0 netns 1  # 移回根命名空间
```



## bridge

```bash
ip link add name br0 type bridge  # 新建网桥
ip link set dev br0 up
ip link set dev eth0 master br0
ip link set dev eth1 master br0  # 添加至网桥

bridge link  # 查看网桥中设备

ip link set dev eth0 nomaster  # 从网桥中删除
ip link del br0  # 删除网桥

```

