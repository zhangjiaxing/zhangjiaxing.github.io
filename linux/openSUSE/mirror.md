Title: openSUSE Leap & Tumbleweed 添加软件源
Date: 2019-12-16 14:55:38
Category: linux
Tags: openSUSE, linux
Slug: openSUSE-addrepo


经测试, aliyun的软件源并不稳定, 更新慢. 经常只更新一部分, 不和官方完全同步.
tsinghuau源, 稳定, 好用.


首先禁用全部仓库：
```sudo zypper mr -da```


如果是Tumbleweed
```bash
sudo zypper ar -fc https://mirrors.tuna.tsinghua.edu.cn/opensuse/tumbleweed/repo/oss        Tumbleweed-Oss-tuna
sudo zypper ar -fc https://mirrors.tuna.tsinghua.edu.cn/opensuse/tumbleweed/repo/non-oss    Tumbleweed-Non-Oss-tuna
sudo zypper ar -fc https://mirrors.tuna.tsinghua.edu.cn/packman/suse/openSUSE_Tumbleweed    Tumbleweed-Packman-tuna

# 更新执行
sudo zypper dup
```


如果是Leap
```bash
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/opensuse/distribution/leap/$releasever/repo/oss/'      repo-oss-tuna
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/opensuse/distribution/leap/$releasever/repo/non-oss'   repo-non-oss-tuna
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/opensuse/update/leap/$releasever/oss'                  repo-update-oss-tuna
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/opensuse/update/leap/$releasever/non-oss'              repo-update-non-oss-tuna
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/packman/suse/openSUSE_Leap_$releasever'                repo-packman-tuna
# 更新执行
sudo zypper update
```

