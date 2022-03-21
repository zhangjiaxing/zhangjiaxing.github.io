Title: dnsmasq DHCP功能和DNS缓存
Date: 2019-07-12 13:59:41
Category: network
Tags: linux, network
Slug: dnsmasq


NetworkManager 热点默认配置:
dnsmasq --conf-file=/dev/null --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.0.1 --dhcp-range=10.42.0.10,10.42.0.254,60m --dhcp-lease-max=50 --dhcp-leasefile=/var/lib/NetworkManager/dnsmasq-wlp8s0.leases --pid-file=/var/run/nm-dnsmasq-wlp8s0.pid --conf-dir=/etc/NetworkManager/dnsmasq-shared.d


dnsmasq HDCP+DNS缓存:
dnsmasq --conf-file=/dev/null --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=127.0.0.1 --dhcp-range=10.42.0.10,10.42.0.254,60m


只做DNS缓存:
dnsmasq --conf-file=/dev/null --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload  --listen-address=127.0.0.1 --cache-size=1000
