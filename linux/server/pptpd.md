Title: linux pptpd配置
Date: 2019-11-14 10:44:33
Category: linux
Tags: linux, server
Slug: linux-pptpd

yum install pptpd


echo "user01  pptpd   123456  * " >>  chap-secrets 


echo "net.ipv4.ip_forward=1" > /etc/sysctl.d/ip_forward.conf
sysctl -p


vim /etc/pptpd.conf
```
localip 192.168.0.1
remoteip        192.168.0.234-238,192.168.0.245
```

systemctl start pptpd.service
