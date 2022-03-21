Title: Linux DNS缓存
Date: 2022-01-04 00:34:54
Category: network
Tags: linux, network
Slug: linux-dns


1. nscd (为glibc提供缓存, 支持glibc 的 getaddrinfo(3), gethostbyname(3) 等相关API)
2. systemd-resolved (1. 通过D-Bus服务提供dns缓存 2. 为glibc提供缓存 3. 在本地回环网口 127.0.0.53 上提供的本地DNS服务器[不推荐])
3. dnsmasq (localhost:53)
4. bind服务 named (localhost:53, 通过查看/etc/resolv.conf nameserver是不是本机地址确认)

