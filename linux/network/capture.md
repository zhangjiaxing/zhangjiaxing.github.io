Title: linux平台下的抓包方案
Date: 2021-08-01 14:47:08
Category: network
Tags: linux, network
Slug: capture

#### linux平台下的抓包方案

- libpcap `wireshark tcpdump均基于此。`
- PF_RING `性能更好。 支持PF_RING ZC模式。`
- DPDK    `性能最好，对硬件有要求。`

