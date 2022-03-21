Title: openSUSE Leap & Tumbleweed 安装解码器
Date: 2020-07-20 23:15:46
Category: linux
Tags: openSUSE, linux
Slug: openSUSE-multimedia


添加全部packman仓库

```bash
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/packman/suse/openSUSE_Leap_$releasever'            packman

# 将系统软件包切换到packman中的软件包(两者混用会导致各种问题)
zypper dup --from packman --allow-vendor-change
```


或者仅仅添加packman中的Essentials(解码器)仓库
```bash
sudo zypper ar -fc 'https://mirrors.tuna.tsinghua.edu.cn/packman/suse/openSUSE_Leap_$releasever/Essentials' packman-essentials

# 将系统软件包切换到packman中的软件包(两者混用会导致各种问题)
zypper dup --from packman-essentials --allow-vendor-change
```


[openSUSE_Additional_package_repositories](https://en.opensuse.org/Additional_package_repositories)

