# Day 8 – Linux Processes & System Monitoring (Technical Support Engineering)

- Welcome to Day 8 of  Linux learning journey!
- Today we dive into one of the most critical concepts for real-world troubleshooting:
- process management and monitoring system performance.

 ## What we Will Learn

## What Linux processes are

## Checking running processes

## Understanding system metrics (CPU, RAM, load average)

## Foreground vs background jobs

- Killing processes

- Using ps, top, htop, kill, free, df, du

## Troubleshooting common high-CPU or memory issues

 ### What is a Process?

- A process is any running program in Linux.

### Each process has:

- PID → Process ID

- PPID → Parent Process ID

- USER → Who started it

- STAT → Process state

- COMMAND → Program being executed

### Viewing Running Processes
 - List All Processes
- ps aux


- Example Output:

 ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.3  21820 12260 ?        Ss   07:52   0:01 /sbin/init
root           2  0.0  0.0   3120  1920 ?        Sl   07:52   0:00 /init
root           9  0.0  0.0   3120  1792 ?        Sl   07:52   0:00 plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate
root          46  0.0  0.3  50452 15616 ?        S<s  07:52   0:00 /usr/lib/systemd/systemd-journald
root          99  0.0  0.1  24876  5760 ?        Ss   07:52   0:01 /usr/lib/systemd/systemd-udevd
systemd+     126  0.0  0.3  21460 12160 ?        Ss   07:52   0:00 /usr/lib/systemd/systemd-resolved
systemd+     128  0.0  0.1  91028  7296 ?        Ssl  07:52   0:00 /usr/lib/systemd/systemd-timesyncd
root         193  0.0  0.0   4236  2432 ?        Ss   07:52   0:00 /usr/sbin/cron -f -P
message+     194  0.0  0.1   9532  4608 ?        Ss   07:52   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --sysl
root         250  0.0  0.2  18156  8320 ?        Ss   07:52   0:00 /usr/lib/systemd/systemd-logind
root         259  0.0  0.3 1756096 12416 ?       Ssl  07:52   0:00 /usr/libexec/wsl-pro-service -vv
root         279  0.0  0.0   3160  1920 hvc0     Ss+  07:52   0:00 /sbin/agetty -o -p -- \u --noclear --keep-baud - 115200,38400,9600 vt220
root         282  0.0  0.0   3116  1792 tty1     Ss+  07:52   0:00 /sbin/agetty -o -p -- \u --noclear - linux
root         284  0.0  0.1   6808  4756 ?        Ss   07:52   0:00 /usr/sbin/apache2 -k start
www-data     288  0.0  0.1 1999324 5028 ?        Sl   07:52   0:00 /usr/sbin/apache2 -k start
www-data     289  0.0  0.1 1933788 5284 ?        Sl   07:52   0:00 /usr/sbin/apache2 -k start
syslog       358  0.0  0.1 222508  5632 ?        Ssl  07:52   0:00 /usr/sbin/rsyslogd -n -iNONE
root         384  0.0  0.5 107024 22144 ?        Ssl  07:52   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-si
root         495  0.0  0.0   3124   896 ?        Ss   07:52   0:00 /init
root         496  0.0  0.0   3140  1156 ?        S    07:52   0:00 /init
mantasha     497  0.0  0.1   6072  4736 pts/0    Ss   07:52   0:00 -bash
root         498  0.0  0.1   6696  4224 pts/1    Ss   07:52   0:00 /bin/login -f
mantasha     546  0.0  0.2  20320 11008 ?        Ss   07:52   0:00 /usr/lib/systemd/systemd --user
mantasha     547  0.0  0.0  21160  3520 ?        S    07:52   0:00 (sd-pam)
mantasha     570  0.0  0.1   6072  4736 pts/1    S+   07:52   0:00 -bash
mantasha    1051 40.0  0.1   8280  4096 pts/0    R+   08:27   0:00 ps aux

---

## Tree View of Processes

- Shows the parent-child hierarchy:

- ps -ef --forest

- output :
ps -ef --forest
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 07:52 ?        00:00:01 /sbin/init
root           2       1  0 07:52 ?        00:00:00 /init
root           9       2  0 07:52 ?        00:00:00  \_ plan9 --control-socket 7 --log-level 4 --server-fd 8 --pipe-fd 10 --log-truncate
root         495       2  0 07:52 ?        00:00:00  \_ /init
root         496     495  0 07:52 ?        00:00:00  |   \_ /init
mantasha     497     496  0 07:52 pts/0    00:00:00  |       \_ -bash
mantasha    1056     497  0 08:28 pts/0    00:00:00  |           \_ ps -ef --forest
root         498       2  0 07:52 pts/1    00:00:00  \_ /bin/login -f
mantasha     570     498  0 07:52 pts/1    00:00:00      \_ -bash
root          46       1  0 07:52 ?        00:00:00 /usr/lib/systemd/systemd-journald
root          99       1  0 07:52 ?        00:00:01 /usr/lib/systemd/systemd-udevd
root        1054      99  0 08:28 ?        00:00:00  \_ (udev-worker)
root        1055      99  0 08:28 ?        00:00:00  \_ (udev-worker)
systemd+     126       1  0 07:52 ?        00:00:00 /usr/lib/systemd/systemd-resolved
systemd+     128       1  0 07:52 ?        00:00:00 /usr/lib/systemd/systemd-timesyncd
root         193       1  0 07:52 ?        00:00:00 /usr/sbin/cron -f -P
message+     194       1  0 07:52 ?        00:00:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
root         250       1  0 07:52 ?        00:00:00 /usr/lib/systemd/systemd-logind
root         259       1  0 07:52 ?        00:00:00 /usr/libexec/wsl-pro-service -vv
root         279       1  0 07:52 hvc0     00:00:00 /sbin/agetty -o -p -- \u --noclear --keep-baud - 115200,38400,9600 vt220
root         282       1  0 07:52 tty1     00:00:00 /sbin/agetty -o -p -- \u --noclear - linux
root         284       1  0 07:52 ?        00:00:00 /usr/sbin/apache2 -k start
www-data     288     284  0 07:52 ?        00:00:00  \_ /usr/sbin/apache2 -k start
www-data     289     284  0 07:52 ?        00:00:00  \_ /usr/sbin/apache2 -k start
syslog       358       1  0 07:52 ?        00:00:00 /usr/sbin/rsyslogd -n -iNONE
root         384       1  0 07:52 ?        00:00:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
mantasha     546       1  0 07:52 ?        00:00:00 /usr/lib/systemd/systemd --user
mantasha     547     546  0 07:52 ?        00:00:00  \_ (sd-pam)

 Real-Time System Monitoring
 top – Live View of Processes
- top
-  top
top - 08:28:40 up 36 min,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  26 total,   1 running,  25 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.1 sy,  0.0 ni, 99.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3856.2 total,   3401.8 free,    458.3 used,    128.0 buff/cache
MiB Swap:   1024.0 total,   1024.0 free,      0.0 used.   3397.9 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
     99 root      20   0   24876   5760   4864 S   0.3   0.1   0:01.41 systemd-udevd
      1 root      20   0   21820  12260   9188 S   0.0   0.3   0:01.43 systemd
      2 root      20   0    3120   1920   1920 S   0.0   0.0   0:00.01 init-systemd(Ub
      9 root      20   0    3120   1792   1792 S   0.0   0.0   0:00.00 init
     46 root      19  -1   50452  15616  14848 S   0.0   0.4   0:00.44 systemd-journal
    126 systemd+  20   0   21460  12160  10240 S   0.0   0.3   0:00.24 systemd-resolve
    128 systemd+  20   0   91028   7296   6528 S   0.0   0.2   0:00.15 systemd-timesyn
    193 root      20   0    4236   2432   2304 S   0.0   0.1   0:00.01 cron
    194 message+  20   0    9532   4608   4224 S   0.0   0.1   0:00.18 dbus-daemon
    250 root      20   0   18156   8320   7424 S   0.0   0.2   0:00.23 systemd-logind
    259 root      20   0 1756096  12416  10496 S   0.0   0.3   0:00.48 wsl-pro-service
    279 root      20   0    3160   1920   1792 S   0.0   0.0   0:00.01 agetty
    282 root      20   0    3116   1792   1664 S   0.0   0.0   0:00.00 agetty
    284 root      20   0    6808   4756   3584 S   0.0   0.1   0:00.20 apache2
    288 www-data  20   0 1999324   5028   3584 S   0.0   0.1   0:00.00 apache2
    289 www-data  20   0 1933788   5284   3712 S   0.0   0.1   0:00.01 apache2
    358 syslog    20   0  222508   5632   4480 S   0.0   0.1   0:00.20 rsyslogd
    384 root      20   0  107024  22144  12928 S   0.0   0.6   0:00.27 unattended-upgr
    495 root      20   0    3124    896    768 S   0.0   0.0   0:00.00 SessionLeader
    496 root      20   0    3140   1156   1024 S   0.0   0.0   0:00.03 Relay(497)
    497 mantasha  20   0    6072   4736   3328 S   0.0   0.1   0:00.11 bash
    498 root      20   0    6696   4224   3584 S   0.0   0.1   0:00.02 login
    546 mantasha  20   0   20320  11008   9088 S   0.0   0.3   0:00.21 systemd
    547 mantasha  20   0   21160   3520   1792 S   0.0   0.1   0:00.00 (sd-pam)
    570 mantasha  20   0    6072   4736   3328 S   0.0   0.1   0:00.05 bash
   1061 mantasha  20   0    9292   5504   3328 R   0.0   0.1   0:00.02 top


#### Displays:

- CPU usage

- Memory usage

- Load average

- Running processes

-  htop – Colorful, Interactive Monitor

- Install:

- sudo apt install htop


- Run:

- htop


- Features:

- Scrollable

- Searchable

- Easy process killing

#### Foreground & Background Jobs
 - Run a program in background:
- ./script.sh &

 #### List background jobs:
- jobs

 - Bring job to foreground:
- fg %1

- Send job to background:

- Press:

Ctrl + Z


- Then:

bg

####  Killing or Stopping Processes
- Kill process by PID:
- kill 1234

- Force kill:
- kill -9 1234

- Kill by name:
- pkill firefox

- Kill all processes with same name:
 - killall python

 #### Checking System Resources
 - Memory Usage:
- free -h

-  Disk Space:
- df -h

 - Folder Size:
du -sh /var/log

 ### CPU Info:
#### lscpu
- output:
lscpu
Architecture:             x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          39 bits physical, 48 bits virtual
  Byte Order:             Little Endian
CPU(s):                   8
  On-line CPU(s) list:    0-7
Vendor ID:                GenuineIntel
  Model name:             Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz
    CPU family:           6
    Model:                142
    Thread(s) per core:   2
    Core(s) per socket:   4
    Socket(s):            1
    Stepping:             12
    BogoMIPS:             3600.00
    Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp
                          lm constant_tsc arch_perfmon rep_good nopl xtopology cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pdcm pcid sse4_1 sse4_2
                           movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpi
                          d ept_ad fsgsbase bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves vnmi md_clear flush_l
                          1d arch_capabilities
Virtualization features:
  Virtualization:         VT-x
  Hypervisor vendor:      Microsoft
  Virtualization type:    full
Caches (sum of all):
  L1d:                    128 KiB (4 instances)
  L1i:                    128 KiB (4 instances)
  L2:                     1 MiB (4 instances)
  L3:                     6 MiB (1 instance)
NUMA:
  NUMA node(s):           1
  NUMA node0 CPU(s):      0-7
Vulnerabilities:
  Gather data sampling:   Unknown: Dependent on hypervisor status
  Itlb multihit:          KVM: Mitigation: VMX disabled
  L1tf:                   Not affected
  Mds:                    Not affected
  Meltdown:               Not affected
  Mmio stale data:        Vulnerable: Clear CPU buffers attempted, no microcode; SMT Host state unknown
  Reg file data sampling: Not affected
  Retbleed:               Mitigation; Enhanced IBRS
  Spec rstack overflow:   Not affected
  Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:             Mitigation; Enhanced / Automatic IBRS; IBPB conditional; RSB filling; PBRSB-eIBRS SW sequence; BHI SW loop, KVM SW loop
  Srbds:                  Unknown: Dependent on hypervisor status
  Tsx async abort:        Not affected

## Common Process Issues & Fixes
 Issue: High CPU Usage

Fix: Identify process:

top


Then kill:

kill -9 <PID>

 Issue: Application Hanging

Fix:

ps aux | grep appname
kill -9 <PID>

 Issue: Low Memory

Fix:
Check memory usage:

free -h
htop

##  Day 8 Summary

Today we learned:

 What Linux processes are

 Viewing processes (ps, top, htop)

 How to run, pause, and background jobs

 Killing & managing processes

 Monitoring CPU, memory, disk usage

Troubleshooting slow or unresponsive systems
