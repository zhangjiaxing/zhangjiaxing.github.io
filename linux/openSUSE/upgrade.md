Title: openSUSE Leap 系统升级
Date: 2020-07-20 23:38:50
Category: linux
Tags: openSUSE, linux
Slug: openSUSE-upgrade


```bash
# 首先启用 repo-update 软件源
zypper modifyrepo --enable repo-update

# 然后更到最新
zypper refresh
zypper update

# 下面的命令建议在tty中执行.  Ctrl + Alt + F2

# 如果 /etc/zypp/repos.d/中定义的Leap 仓库已经使用$releasever变量时, 则使用:
zypper --releasever=15.2 ref


# 或者仓库地址使用特定的Leap版本号对它们进行硬编码，则需要首先对其进行修改:
sudo sed -i 's/15.1/$releasever/g' /etc/zypp/repos.d/*.repo
# 然后执行:
zypper --releasever=15.2 ref
zypper --releasever=15.2 dup


# 最后重新启动系统.

```

