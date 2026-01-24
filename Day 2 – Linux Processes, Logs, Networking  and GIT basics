# Day 2 – Linux Processes, Logs, Networking & Git Basics

## Objective
Learn real-world Linux process management, system log analysis, networking troubleshooting workflow, and basic Git usage required for Technical Support / Cloud Support roles.

---

## Part 1 – Linux Process Management

## Commands Practiced
ps
ps aux
top
htop
kill <PID>
kill -9 <PID>
sleep 300 &

---

### Key Learnings

- A **process** is a running program in Linux.
- `ps` shows processes in the current terminal session.
- `ps aux` shows **all running processes** with CPU and memory usage.
- `top` and `htop` provide real-time monitoring of system resource usage.
- `kill PID` gracefully stops a process.
- `kill -9 PID` forcefully terminates a process if it is unresponsive.
- Background processes can be started using `&`.

---

### Command Outputs

#### ps 
PID TTY          TIME CMD
    492 pts/2    00:00:00 bash
    995 pts/2    00:00:00 ps

### ps aux
ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.4  0.3  21860 12344 ?        Ss   12:09   0:01 /sbin/init
root           2  0.0  0.0   3120  1920 ?        Sl   12:09   0:00 /init
root           9  0.0  0.0   3120  1792 ?        Sl   12:09   0:00 plan9 --control-socket 7 --log-level 4 --server-fd 8
root          45  0.1  0.3  42236 15488 ?        S<s  12:09   0:00 /usr/lib/systemd/systemd-journald
root          98  0.1  0.1  25136  6272 ?        Ss   12:09   0:00 /usr/lib/systemd/systemd-udevd
systemd+     155  0.0  0.3  21456 12544 ?        Ss   12:09   0:00 /usr/lib/systemd/systemd-resolved
systemd+     159  0.0  0.1  91024  7552 ?        Ssl  12:09   0:00 /usr/lib/systemd/systemd-timesyncd
root         168  0.0  0.0   4236  2432 ?        Ss   12:09   0:00 /usr/sbin/cron -f -P
message+     169  0.0  0.1   9664  4736 ?        Ss   12:09   0:00 @dbus-daemon --system --address=systemd: --nofork --n
root         182  0.0  0.2  17968  8064 ?        Ss   12:09   0:00 /usr/lib/systemd/systemd-logind
root         184  0.0  0.3 1682108 11904 ?       Ssl  12:09   0:00 /usr/libexec/wsl-pro-service -vv
root         200  0.0  0.0   3160  1920 hvc0     Ss+  12:09   0:00 /sbin/agetty -o -p -- \u --noclear --keep-baud - 1152
syslog       204  0.0  0.1 222508  5504 ?        Ssl  12:09   0:00 /usr/sbin/rsyslogd -n -iNONE
root         206  0.0  0.0   3116  1792 tty1     Ss+  12:09   0:00 /sbin/agetty -o -p -- \u --noclear - linux
root         213  0.0  0.5 107032 22272 ?        Ssl  12:09   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unatt
root         308  0.0  0.0   3124   896 ?        Ss   12:09   0:00 /init
root         309  0.0  0.0   3140  1156 ?        S    12:09   0:00 /init
mantasha     311  0.0  0.1   6072  5120 pts/0    Ss+  12:09   0:00 -bash
root         313  0.0  0.1   6696  4224 pts/1    Ss   12:09   0:00 /bin/login -f
mantasha     361  0.0  0.2  20336 11136 ?        Ss   12:09   0:00 /usr/lib/systemd/systemd --user
mantasha     362  0.0  0.0  21156  3520 ?        S    12:09   0:00 (sd-pam)
mantasha     388  0.0  0.1   6072  4864 pts/1    S+   12:09   0:00 -bash
root         487  0.0  0.0   3136   904 ?        Ss   12:09   0:00 /init
root         489  0.0  0.0   3136  1168 ?        S    12:09   0:00 /init
mantasha     492  0.0  0.1   6072  5248 pts/2    Ss   12:09   0:00 -bash
root         754  0.0  0.5 370084 20480 ?        Ssl  12:10   0:00 /usr/libexec/packagekitd
polkitd      759  0.0  0.1 308164  7680 ?        Ssl  12:10   0:00 /usr/lib/polkit-1/polkitd --no-debug
mantasha     996  0.0  0.1   8280  4096 pts/2    R+   12:13   0:00 ps aux


### top / htop 
 top
top - 12:13:44 up 19 min,  1 user,  load average: 0.23, 0.15, 0.06
Tasks:  30 total,   1 running,  29 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3856.2 total,   3387.0 free,    476.6 used,    121.1 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3379.6 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    997 mantasha  20   0    9272   5504   3328 R   0.7   0.1   0:00.03 top
      1 root      20   0   21860  12344   9272 S   0.0   0.3   0:01.08 systemd
      2 root      20   0    3120   1920   1920 S   0.0   0.0   0:00.02 init-systemd(Ub
      9 root      20   0    3120   1792   1792 S   0.0   0.0   0:00.00 init
     45 root      19  -1   42236  15488  14592 S   0.0   0.4   0:00.27 systemd-journal
     98 root      20   0   25136   6272   4864 S   0.0   0.2   0:00.33 systemd-udevd
    155 systemd+  20   0   21456  12544  10496 S   0.0   0.3   0:00.13 systemd-resolve
    159 systemd+  20   0   91024   7552   6784 S   0.0   0.2   0:00.07 systemd-timesyn
    168 root      20   0    4236   2432   2304 S   0.0   0.1   0:00.01 cron
    169 message+  20   0    9664   4736   4352 S   0.0   0.1   0:00.12 dbus-daemon
    182 root      20   0   17968   8064   7296 S   0.0   0.2   0:00.13 systemd-logind
    184 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.17 wsl-pro-service
    200 root      20   0    3160   1920   1792 S   0.0   0.0   0:00.01 agetty
    204 syslog    20   0  222508   5504   4352 S   0.0   0.1   0:00.10 rsyslogd
    206 root      20   0    3116   1792   1664 S   0.0   0.0   0:00.01 agetty
    213 root      20   0  107032  22272  12928 S   0.0   0.6   0:00.18 unattended-upgr
    308 root      20   0    3124    896    768 S   0.0   0.0   0:00.00 SessionLeader
    309 root      20   0    3140   1156   1024 S   0.0   0.0   0:00.00 Relay(311)
    311 mantasha  20   0    6072   5120   3584 S   0.0   0.1   0:00.08 bash
    313 root      20   0    6696   4224   3712 S   0.0   0.1   0:00.03 login
    361 mantasha  20   0   20336  11136   9088 S   0.0   0.3   0:00.24 systemd
    362 mantasha  20   0   21156   3520   1792 S   0.0   0.1   0:00.00 (sd-pam)
    388 mantasha  20   0    6072   4864   3328 S   0.0   0.1   0:00.05 bash
    487 root      20   0    3136    904    768 S   0.0   0.0   0:00.00 SessionLeader
    489 root      20   0    3136   1296   1152 S   0.0   0.0   0:00.07 Relay(492)
    492 mantasha  20   0    6072   5248   3584 S   0.0   0.1   0:00.12 bash
    754 root      20   0  370084  20480  17536 S   0.0   0.5   0:00.09 packagekitd
    759 polkitd   20   0  308164   7680   6912 S   0.0   0.2   0:00.13 polkitd
    998 root      20   0   25140   3608   2176 S   0.0   0.1   0:00.00 (udev-worker)
    999 root      20   0   25140   3608   2176 S   0.0   0.1   0:00.00 (udev-worker)
top - 12:13:46 up 19 min,  1 user,  load average: 0.21, 0.14, 0.06
Threads:  47 total,   1 running,  46 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3856.2 total,   3386.7 free,    476.8 used,    121.1 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3379.4 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    997 mantasha  20   0    9400   5504   3328 R  18.2   0.1   0:00.04 top
      1 root      20   0   21860  12344   9272 S   0.0   0.3   0:01.08 systemd
      2 root      20   0    3120   1920   1920 S   0.0   0.0   0:00.01 init-systemd(Ub
     11 root      20   0    3120   1920   1920 S   0.0   0.0   0:00.00 Interop
      9 root      20   0    3120   1792   1792 S   0.0   0.0   0:00.00 init
     10 root      20   0    3120   1792   1792 S   0.0   0.0   0:00.00 init
     45 root      19  -1   42236  15488  14592 S   0.0   0.4   0:00.26 systemd-journal
     98 root      20   0   25136   6272   4864 S   0.0   0.2   0:00.33 systemd-udevd
    155 systemd+  20   0   21456  12544  10496 S   0.0   0.3   0:00.13 systemd-resolve
    159 systemd+  20   0   91024   7552   6784 S   0.0   0.2   0:00.08 systemd-timesyn
    163 systemd+  20   0   91024   7552   6784 S   0.0   0.2   0:00.00 sd-resolve
    168 root      20   0    4236   2432   2304 S   0.0   0.1   0:00.01 cron
    169 message+  20   0    9664   4736   4352 S   0.0   0.1   0:00.12 dbus-daemon
    182 root      20   0   17968   8064   7296 S   0.0   0.2   0:00.13 systemd-logind
    184 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.12 wsl-pro-service
    214 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.01 wsl-pro-service
    215 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.01 wsl-pro-service
    216 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.00 wsl-pro-service
    217 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.00 wsl-pro-service
    218 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.00 wsl-pro-service
    229 root      20   0 1682108  11904  10112 S   0.0   0.3   0:00.01 wsl-pro-service
    200 root      20   0    3160   1920   1792 S   0.0   0.0   0:00.01 agetty
    204 syslog    20   0  222508   5504   4352 S   0.0   0.1   0:00.06 rsyslogd
    222 syslog    20   0  222508   5504   4352 S   0.0   0.1   0:00.01 in:imuxsock
    223 syslog    20   0  222508   5504   4352 S   0.0   0.1   0:00.00 in:imklog
    224 syslog    20   0  222508   5504   4352 S   0.0   0.1   0:00.01 rs:main Q:Reg
    206 root      20   0    3116   1792   1664 S   0.0   0.0   0:00.01 agetty
    213 root      20   0  107032  22272  12928 S   0.0   0.6   0:00.18 unattended-upgr
    261 root      20   0  107032  22272  12928 S   0.0   0.6   0:00.00 gmain
    308 root      20   0    3124    896    768 S   0.0   0.0   0:00.00 SessionLeader
    309 root      20   0    3140   1156   1024 S   0.0   0.0   0:00.00 Relay(311)
    311 mantasha  20   0    6072   5120   3584 S   0.0   0.1   0:00.08 bash
    313 root      20   0    6696   4224   3712 S   0.0   0.1   0:00.02 login
    361 mantasha  20   0   20336  11136   9088 S   0.0   0.3   0:00.24 systemd


### cat /var/log/syslog
 cat /var/log/syslog
2026-01-21T08:54:23.409314+00:00 DESKTOP-AK8I671 systemd[1]: Finished systemd-modules-load.service - Load Kernel Modules.
2026-01-21T08:54:23.410173+00:00 DESKTOP-AK8I671 kernel: Linux version 6.6.87.2-microsoft-standard-WSL2 (root@439a258ad544) (gcc (GCC) 11.2.0, GNU ld (GNU Binutils) 2.37) #1 SMP PREEMPT_DYNAMIC Thu Jun  5 18:30:46 UTC 2025
2026-01-21T08:54:23.410234+00:00 DESKTOP-AK8I671 kernel: Command line: initrd=\initrd.img WSL_ROOT_INIT=1 panic=-1 nr_cpus=8 hv_utils.timesync_implicit=1 console=hvc0 debug pty.legacy_count=0 WSL_ENABLE_CRASH_DUMP=1
2026-01-21T08:54:23.410239+00:00 DESKTOP-AK8I671 kernel: KERNEL supported cpus:
2026-01-21T08:54:23.410240+00:00 DESKTOP-AK8I671 kernel:   Intel GenuineIntel
2026-01-21T08:54:23.410241+00:00 DESKTOP-AK8I671 kernel:   AMD AuthenticAMD
2026-01-21T08:54:23.409664+00:00 DESKTOP-AK8I671 systemd[1]: Finished systemd-remount-fs.service - Remount Root and Kernel File Systems.
2026-01-21T08:54:23.410260+00:00 DESKTOP-AK8I671 systemd[1]: Finished keyboard-setup.service - Set the console keyboard layout.
2026-01-21T08:54:23.410276+00:00 DESKTOP-AK8I671 systemd[1]: Mounting sys-fs-fuse-connections.mount - FUSE Control File System...
2026-01-21T08:54:23.410283+00:00 DESKTOP-AK8I671 systemd[1]: Mounting sys-kernel-config.mount - Kernel Configuration File System...
2026-01-21T08:54:23.410289+00:00 DESKTOP-AK8I671 systemd[1]: systemd-hwdb-update.service - Rebuild Hardware Database was skipped because no trigger condition checks were met.


### grep error /var/log/syslog
2026-01-21T08:54:23.410974+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.path - Process error reports when automatic reporting is enabled (file watch) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
2026-01-21T08:54:23.411022+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.timer - Process error reports when automatic reporting is enabled (timer based) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
2026-01-21T08:54:23.849963+00:00 DESKTOP-AK8I671 snapd[196]: helpers.go:159: error trying to compare the snap system key: system-key missing on disk
2026-01-22T08:15:54.617777+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.path - Process error reports when automatic reporting is enabled (file watch) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
2026-01-22T08:15:54.617784+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.timer - Process error reports when automatic reporting is enabled (timer based) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
2026-01-24T12:09:10.959728+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.path - Process error reports when automatic reporting is enabled (file watch) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
2026-01-24T12:09:10.959737+00:00 DESKTOP-AK8I671 systemd[1]: apport-autoreport.timer - Process error reports when automatic reporting is enabled (timer based) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).


### grep failed /var/log/syslog
2026-01-21T08:54:23.415412+00:00 DESKTOP-AK8I671 kernel: ACPI: _OSC evaluation for CPUs failed, trying _PDC
2026-01-21T08:54:23.415898+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-21T08:54:23.415901+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_is_feature_enabled: Ioctl failed: -22
2026-01-21T08:54:23.415902+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22
2026-01-21T08:54:23.415914+00:00 DESKTOP-AK8I671 kernel: message repeated 3 times: [ misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22]
2026-01-21T08:54:23.415916+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -2
2026-01-21T09:40:24.730939+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-21T09:48:13.371724+00:00 DESKTOP-AK8I671 python3[952]: ["2026-01-21T09:48:13.371", "WARNING", "ubuntupro.system", "get_kernel_info", 166, "failed to process /proc/version_signature.", {}]
2026-01-21T09:50:36.048267+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-21T11:51:35.015968+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-21T12:53:40.789288+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-21T13:04:17.852882+00:00 DESKTOP-AK8I671 kernel: WSL (217) ERROR: CheckConnection: connect() failed: 101
2026-01-22T08:15:54.619030+00:00 DESKTOP-AK8I671 kernel: ACPI: _OSC evaluation for CPUs failed, trying _PDC
2026-01-22T08:15:54.619787+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_is_feature_enabled: Ioctl failed: -22
2026-01-22T08:15:54.619788+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22
2026-01-22T08:15:54.619795+00:00 DESKTOP-AK8I671 kernel: message repeated 3 times: [ misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22]
2026-01-22T08:15:54.619796+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -2
2026-01-22T08:15:57.061319+00:00 DESKTOP-AK8I671 kernel: WSL (216) ERROR: CheckConnection: connect() failed: 101
2026-01-24T12:09:10.959762+00:00 DESKTOP-AK8I671 kernel: ACPI: _OSC evaluation for CPUs failed, trying _PDC
2026-01-24T12:09:10.960325+00:00 DESKTOP-AK8I671 kernel: WSL (1 - init(docker-desktop)) ERROR: ConfigApplyWindowsLibPath:2092: open /etc/ld.so.conf.d/ld.wsl.conf failed 2
2026-01-24T12:09:10.960328+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_is_feature_enabled: Ioctl failed: -22
2026-01-24T12:09:10.960329+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22
2026-01-24T12:09:10.960336+00:00 DESKTOP-AK8I671 kernel: message repeated 3 times: [ misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22]
2026-01-24T12:09:10.960337+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -2
2026-01-24T12:09:10.960350+00:00 DESKTOP-AK8I671 kernel: WSL (213) ERROR: CheckConnection: connect() failed: 101
2026-01-24T12:09:10.960397+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_is_feature_enabled: Ioctl failed: -22
2026-01-24T12:09:10.960398+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22
2026-01-24T12:09:10.960402+00:00 DESKTOP-AK8I671 kernel: message repeated 3 times: [ misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -22]
2026-01-24T12:09:10.960403+00:00 DESKTOP-AK8I671 kernel: misc dxg: dxgk: dxgkio_query_adapter_info: Ioctl failed: -2


###  grep denied /var/log/syslog
2026-01-21T08:54:23.410552+00:00 DESKTOP-AK8I671 sh[129]: /bin/sh: 1: cannot create /proc/sys/fs/binfmt_misc/WSLInterop: Permission denied
2026-01-22T08:15:54.617617+00:00 DESKTOP-AK8I671 sh[131]: /bin/sh: 1: cannot create /proc/sys/fs/binfmt_misc/WSLInterop: Permission denied
2026-01-24T12:09:10.959311+00:00 DESKTOP-AK8I671 sh[106]: /bin/sh: 1: cannot create /proc/sys/fs/binfmt_misc/WSLInterop: Permission denied

###  ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet 10.255.255.254/32 brd 10.255.255.254 scope global lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1400 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:06:5b:69 brd ff:ff:ff:ff:ff:ff
    inet 192.168.193.240/20 brd 192.168.207.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fe06:5b69/64 scope link
       valid_lft forever preferred_lft forever

###  ip route
default via 192.168.192.1 dev eth0 proto kernel
192.168.192.0/20 dev eth0 proto kernel scope link src 192.168.193.240

### ss -tulnp
Netid          State           Recv-Q          Send-Q                    Local Address:Port                     Peer Address:Port          Process
udp            UNCONN          0               0                            127.0.0.54:53                            0.0.0.0:*
udp            UNCONN          0               0                         127.0.0.53%lo:53                            0.0.0.0:*
udp            UNCONN          0               0                        10.255.255.254:53                            0.0.0.0:*
udp            UNCONN          0               0                             127.0.0.1:323                           0.0.0.0:*
udp            UNCONN          0               0                                 [::1]:323                              [::]:*
tcp            LISTEN          0               1000                     10.255.255.254:53                            0.0.0.0:*
tcp            LISTEN          0               4096                      127.0.0.53%lo:53                            0.0.0.0:*
tcp            LISTEN          0               4096                         127.0.0.54:53                            0.0.0.0:*


### ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=111 time=194 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=111 time=149 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=111 time=136 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=111 time=131 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=111 time=142 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=111 time=187 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=111 time=287 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=111 time=140 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=111 time=227 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=111 time=141 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=111 time=140 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=111 time=266 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=111 time=174 ms
^C
--- 8.8.8.8 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12020ms
rtt min/avg/max/mdev = 130.703/177.972/286.656/50.119 ms

### curl https://google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>

## Networking Troubleshooting Method Used

1. Checked IP address using `ip a`
2. Verified default gateway using `ip route`
3. Tested internet connectivity using `ping 8.8.8.8`
4. Verified DNS and HTTP access using `curl https://google.com`
5. Checked listening services using `ss -tulnp`

Conclusion: Network connectivity and DNS resolution were working correctly.


## Part 3 – Git Basics

### Git Commands Used
git status
git add day2.md
git commit -m "Day 2: Linux processes, logs, networking troubleshooting"
git push

### Key Learnings

- Git is used to track changes in projects.
- `git status` shows modified files.
- `git add` stages changes.
- `git commit` saves changes locally.
- `git push` uploads changes to GitHub.


## Issues Faced & Fixes

### Issue 1: curl command not found

Error:
curl: not found

Fix:
Installed curl using:

sudo apt install curl

### Issue 2: WSL permission denied error

Error:
cannot create /proc/sys/fs/binfmt_misc/WSLInterop: Permission denied
Cause:
System-level restriction in WSL.

Fix:
No action required. Ignored as it does not affect networking or user applications.

---
### Issue 3: WSL connection errors in syslog

Error:
WSL ERROR: CheckConnection: connect() failed: 101

Fix:
Restarted WSL using:

wsl --shutdown

Then reopened terminal.


## Summary

On Day 2, I practiced real-world Linux support engineering tasks including:

- Monitoring and managing system processes using ps, top, and htop
- Analyzing system logs to identify errors, failures, and permission issues
- Performing structured network troubleshooting using industry-standard tools
- Validating DNS, routing, and internet connectivity
- Using Git for version control and documentation


This hands-on practice strengthened my foundation for Technical Support and Cloud Support Engineer roles.
