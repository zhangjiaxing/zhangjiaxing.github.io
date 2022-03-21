Title: SysRq
Date: 2017-12-29 14:20:16
Category: linux
Tags: linux
Slug: linux-sysrq

##SysRq HELP

#####开启这个功能
```bash
echo 1 > /proc/sys/kernel/sysrq  # 或者在 /etc/sysctl.conf 中设置 kernel.sysrq=1
```

#####用法1: 
```bash
echo b > /proc/sysrq-trigger
```

#####用法2:
```bash
Alt + SysRq + b  # SysRq 键在x86上一般为 [print screen] 键
```

#####命令介绍
```
loglevel(0-9)
reboot(b)
crash(c)
terminate-all-tasks(e)
memory-full-oom-kill(f)
kill-all-tasks(i)
thaw-filesystems(j)
sak(k)
show-backtrace-all-active-cpus(l)
show-memory-usage(m)
nice-all-RT-tasks(n)
poweroff(o)
show-registers(p)
show-all-timers(q)
unraw(r)
sync(s)
show-task-states(t)
unmount(u)
force-fb(V)
show-blocked-tasks(w)
dump-ftrace-buffer(z)
```
