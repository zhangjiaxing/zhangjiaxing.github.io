Title: openSUSE Tumbleweed server 安装cinnamon桌面
Date: 2019-12-19 11:11:01
Category: linux
Tags: openSUSE, linux
Slug: openSUSE-server-install-cinnamon


```bash
zypper refresh
zypper install cinnamon
zypper install lightdm
zypper install xorg-x11-server
zypper install xorg-x11-server-wayland
update-alternatives --list default-displaymanager
update-alternatives --config default-displaymanager 选择lightdm
systemctl disable default.target  # 或者删除 /etc/systemd/system/default.target
ln -s /usr/lib/systemd/system/graphical.target /etc/systemd/system/default.target

zypper install wqy-microhei-fonts

# 然后安装输入法
zypper install fcitx-libpinyin fcitx-config-gtk3

reboot
```
