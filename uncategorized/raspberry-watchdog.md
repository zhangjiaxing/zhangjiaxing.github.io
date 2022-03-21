Title: raspberry watchdog
Date: 2019-11-22 20:06:38
Category: linux
Tags: linux, raspberry
Slug: raspberry-watchdog


raspberry 4b
Raspbian GNU/Linux 10 (buster)

> `ls /dev/watchdog*`
> > /dev/watchdog  /dev/watchdog0

> grep Watchdog /etc/systemd/system.conf
> > RuntimeWatchdogSec=10
> > ShutdownWatchdogSec=10min

> systemctl daemon-reexec

> :(){ :|:& };:

