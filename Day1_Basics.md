# Day 1 – Linux Basics & Networking Fundamentals

## Objective
Learn basic Linux commands and understand core networking checks used in technical support.

---

## Linux Commands Practiced

pwd
ls
mkdir
cd
touch
echo
cat
df -h
free -h
ip a
ping



---

## Command Outputs

## ls 
3D Objects
AppData
Application Data
Cisco Packet Tracer 7.3.0
Contacts
Cookies
CrossDevice
Desktop
Documents
Downloads
Favorites
IntelGraphicsProfiles
Links
Local Settings
Music
My Documents
NTUSER.DAT
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TM.blf
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TMContainer00000000000000000001.regtrans-ms
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TMContainer00000000000000000002.regtrans-ms
NetHood
OneDrive
Pictures
Postman
Postman Agent
PrintHood
Recent
Saved Games
Searches
SendTo
Start Menu
Templates
Videos
VirtualBox VMs
c
gpt4all
linux_practise
ntuser.dat.LOG1
ntuser.dat.LOG2
ntuser.ini
test.db
this
training_data.csv
users
wekafiles

# pwd
/mnt/host/c/Users/dev

#cd
DESKTOP-----:/mnt/host/c/Users/dev# cd ..
DESKTOP------:/mnt/host/c/Users#

#ls -a
.
..
.VirtualBox
.docker
.dotnet
.hackerearth
.ipython
.keras
.matplotlib
.ms-ad
.nbi
.node_repl_history
.oracle_jre_usage
.packettracer
.streamlit
.virtualenvs
.vscode
3D Objects
AppData
Application Data
Cisco Packet Tracer 7.3.0
Contacts
Cookies
CrossDevice
Desktop
Documents
Downloads
Favorites
IntelGraphicsProfiles
Links
Local Settings
Music
My Documents
NTUSER.DAT
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TM.blf
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TMContainer00000000000000000001.regtrans-ms
NTUSER.DAT{2ad838bc-efea-11ee-a54d-000d3a94eaa1}.TMContainer00000000000000000002.regtrans-ms
NetHood
OneDrive
Pictures
Postman
Postman Agent
PrintHood
Recent
Saved Games
Searches
SendTo
Start Menu
Templates
Videos

~
~
~
~
~
~
~
~
~
~
~
~
Mem: 313364K used, 3635404K free, 3040K shrd, 664K buff, 36736K cached
CPU:   0% usr   0% sys   0% nic 100% idle   0% io   0% irq   0% sirq
Load average: 0.00 0.00 0.00 2/162 34
  PID  PPID USER     STAT   VSZ %VSZ CPU %CPU COMMAND
   11    10 root     S     3140   0%   4   0% {Relay(12)} /init
   10     1 root     S     3124   0%   2   0% {SessionLeader} /init
    1     0 root     S     3120   0%   6   0% {init(docker-des} /init
    7     1 root     S     3120   0%   3   0% {init} plan9 --control-socket 6 --log-level 4 --server-fd 7 --pipe-fd 9 --log-truncate
   12    11 root     S     1700   0%   3   0% -sh
   34    12 root     R     1624   0%   6   0% top

#free -h 
DESKTOP-----1:/mnt/host/c/Users/dev/linux_practise# free -h
              total        used        free      shared  buff/cache   available
Mem:           3.8G      262.1M        3.5G        3.0M       43.9M        3.4G
Swap:          1.0G           0        1.0G

   34    12 root     R     1624   0%   6   0% top
DESKTOP------1:/mnt/host/c/Users/dev/linux_practise# free -h
              total        used        free      shared  buff/cache   available
Mem:           3.8G      262.1M        3.5G        3.0M       43.9M        3.4G
Swap:          1.0G           0        1.0G
DESKTOP------1:/mnt/host/c/Users/dev/linux_practise# df -h
Filesystem                Size      Used Available Use% Mounted on
none                      1.9G         0      1.9G   0% /lib/modules/6.6.87.2-microsoft-standard-WSL2
none                      1.9G      4.0K      1.9G   0% /mnt/host/wsl
drivers                 237.5G    147.0G     90.5G  62% /usr/lib/wsl/drivers
/dev/sdd               1006.9G     56.3M    955.6G   0% /
none                      1.9G     72.0K      1.9G   0% /mnt/host/wslg
/dev/sdd               1006.9G     56.3M    955.6G   0% /mnt/host/wslg/distro
none                      1.9G         0      1.9G   0% /usr/lib/wsl/lib
none                      1.9G         0      1.9G   0% /dev
none                      1.9G         0      1.9G   0% /run
none                      1.9G         0      1.9G   0% /run/lock
none                      1.9G         0      1.9G   0% /run/shm
none                      1.9G         0      1.9G   0% /dev/shm
none                      1.9G         0      1.9G   0% /run/user
none                      1.9G     72.0K      1.9G   0% /tmp/.X11-unix
C:\                     237.5G    147.0G     90.5G  62% /mnt/host/c
D:\                     527.5G     73.6G    454.0G  14% /mnt/host/d
none                      1.9G     76.0K      1.9G   0% /mnt/host/wslg/versions.txt
none                      1.9G     76.0K      1.9G   0% /mnt/host/wslg/doc
E:\                     100.0M     64.3M     35.7M  64% /mnt/host/e
F:\                      97.7G     38.9G     58.7G  40% /mnt/host/f
DESKTOP-------1:/mnt/host/c/Users/dev/linux_practise# uptime
 10:22:24 up 11 min,  0 users,  load average: 0.00, 0.00, 0.00
DESKTOP-------1:/mnt/host/c/Users/dev/linux_practise# ps
PID   USER     TIME  COMMAND
    1 root      0:00 {init(docker-des} /init
    7 root      0:00 {init} plan9 --control-socket 6 --log-level 4 --server-fd 7 --pipe-fd 9 --log-truncate
   10 root      0:00 {SessionLeader} /init
   11 root      0:00 {Relay(12)} /init
   12 root      0:00 -sh
   38 root      0:00 ps
DESKTOP------1:/mnt/host/c/Users/dev/linux_practise# ps aux
PID   USER     TIME  COMMAND
    1 root      0:00 {init(docker-des} /init
    7 root      0:00 {init} plan9 --control-socket 6 --log-level 4 --server-fd 7 --pipe-fd 9 --log-truncate
   10 root      0:00 {SessionLeader} /init
   11 root      0:00 {Relay(12)} /init
   12 root      0:00 -sh
   39 root      0:00 ps aux
DESKTOP-------1:/mnt/host/c/Users/dev/linux_practise# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet 10.255.255.254/32 brd 10.255.255.254 scope global lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1400 qdisc mq state UP qlen 1000
    link/ether 00:15:5d:06:55:fe brd ff:ff:ff:ff:ff:ff
    inet 192.168.193.240/20 brd 192.168.207.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fe06:55fe/64 scope link
       valid_lft forever preferred_lft forever
DESKTOP-------1:/mnt/host/c/Users/dev/linux_practise# ip google
BusyBox v1.36.1 (2024-05-21 13:38:37 UTC) multi-call binary.

Usage: ip [OPTIONS] address|route|link|tunnel|neigh|rule [ARGS]

OPTIONS := -f[amily] inet|inet6|link | -o[neline]

ip addr add|del IFADDR dev IFACE | show|flush [dev IFACE] [to PREFIX]
ip route list|flush|add|del|change|append|replace|test ROUTE
ip link set IFACE [up|down] [arp on|off] [multicast on|off]
        [promisc on|off] [mtu NUM] [name NAME] [qlen NUM] [address MAC]
        [master IFACE | nomaster] [netns PID]
ip tunnel add|change|del|show [NAME]
        [mode ipip|gre|sit] [remote ADDR] [local ADDR] [ttl TTL]
ip neigh show|flush [to PREFIX] [dev DEV] [nud STATE]
ip rule [list] | add|del SELECTOR ACTION
DESKTOP-AK8I671:/mnt/host/c/Users/dev/linux_practise# ping google.com
PING google.com (142.251.43.110): 56 data bytes
64 bytes from 142.251.43.110: seq=0 ttl=111 time=74.973 ms
64 bytes from 142.251.43.110: seq=1 ttl=111 time=50.611 ms
64 bytes from 142.251.43.110: seq=2 ttl=111 time=51.480 ms
64 bytes from 142.251.43.110: seq=3 ttl=111 time=39.280 ms
64 bytes from 142.251.43.110: seq=4 ttl=111 time=38.778 ms
64 bytes from 142.251.43.110: seq=5 ttl=111 time=49.326 ms
64 bytes from 142.251.43.110: seq=6 ttl=111 time=39.025 ms
64 bytes from 142.251.43.110: seq=7 ttl=111 time=39.619 ms
64 bytes from 142.251.43.110: seq=8 ttl=111 time=43.614 ms
64 bytes from 142.251.43.110: seq=9 ttl=111 time=37.084 ms
64 bytes from 142.251.43.110: seq=10 ttl=111 time=46.988 ms
64 bytes from 142.251.43.110: seq=11 ttl=111 time=47.889 ms
^C
--- google.com ping statistics ---
13 packets transmitted, 12 packets received, 7% packet loss
round-trip min/avg/max = 37.084/46.555/74.973 ms


DESKTOP-------:/mnt/host/c/Users/dev/linux_practise# cd ..

DESKTOP-AK8I671:/mnt/host/c/Users/dev# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet 10.255.255.254/32 brd 10.255.255.254 scope global lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1400 qdisc mq state UP qlen 1000
    link/ether 00:15:5d:06:55:fe brd ff:ff:ff:ff:ff:ff
    inet 192.168.193.240/20 brd 192.168.207.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fe06:55fe/64 scope link
       valid_lft forever preferred_lft forever
DESKTOP-------1:/mnt/host/c/Users/dev# ns lookup google.com
-sh: ns: not found
DESKTOP-------1:/mnt/host/c/Users/dev# nslookup google.com
Server:         10.255.255.254
Address:        10.255.255.254:53

Non-authoritative answer:
Name:   google.com
Address: 142.250.182.110

Non-authoritative answer:
Name:   google.com
Address: 2404:6800:4002:81a::200e


##Networking Concepts Learned

IP address identifies a device in a network

DNS resolves domain names to IP addresses

Ping checks connectivity

Ports define services (80 HTTP, 443 HTTPS)

TCP is reliable, UDP is fast

OSI model layers overview



## Issues Faced & Fixes

### Issue 1: curl command not found
Error:
-sh: curl: not found

Fix:
curl package was not installed in the Linux environment.  
Installed it using:
sudo apt update  
sudo apt install curl
After installation, verified using:
curl google.com

---

### Issue 2: Directory not found when using `cd dev`
Error:
cd: can't cd to dev: No such file or directory

Fix:
Used `ls` command to check existing directories before navigating.  
Learned that Linux paths are case-sensitive and the directory must exist.

---

### Issue 3: Incorrect command `cd/`
Error:
cd/: not found

Fix:
Correct command is:
cd /

Learned that there must be a space between `cd` and `/`.



