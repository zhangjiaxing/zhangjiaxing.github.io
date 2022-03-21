Title: linux 使用network manager 开启wifi热点
Date: 2018-04-13 19:42:58
Category: linux
Tags: wireless, linux
Slug: networkmanager-wifi-ap


linux 使用network manager 开启wifi热点

```
开启热点
nmcli device wifi hotspot  ssid zhiliao-test  password 12345678
或者
nmcli device wifi hotspot con-name zhiliao-test-5G ssid zhiliao-test-5G band a password 12345678

删除热点配置
nmcli connection show
nmcli  connection delete zhiliao-test-5G
```

