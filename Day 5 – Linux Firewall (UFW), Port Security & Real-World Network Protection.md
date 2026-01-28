# Day 5 – Linux Firewall (UFW), Port Security & Real-World Network Protection

## Objective

Learn how to secure a Linux system by:

- Understanding firewalls
- Using UFW (Uncomplicated Firewall)
- Controlling ports and services
- Testing real traffic blocking
- Practicing real support-engineer troubleshooting

---

## Part 1 – Firewall Basics (Theory)

### What is a Firewall?

A firewall controls **incoming and outgoing network traffic** based on security rules.

It helps to:

- Block unauthorized access
- Protect servers from attacks
- Allow only required services (SSH, HTTP, etc.)

---

### Types of Firewalls

| Type | Description |
|------|------------|
| Network Firewall | Protects entire networks |
| Host Firewall | Protects individual machines |
| Hardware Firewall | Physical device |
| Software Firewall | OS-based (UFW, iptables) |

Linux uses **iptables/nftables internally**.  
UFW is a **simple interface** on top of them.

---

## Part 2 – Installing UFW (Practical)

### Command

- sudo apt update

-  sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:5 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [1410 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [1700 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en [314 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [175 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 c-n-f Metadata [16.0 kB]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1519 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [310 kB]
Get:12 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [386 kB]
Get:13 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [2506 kB]
Get:14 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [229 kB]
Get:15 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [21.5 kB]
Get:16 http://security.ubuntu.com/ubuntu noble-security/main amd64 c-n-f Metadata [9820 B]
Get:17 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [924 kB]
Get:18 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [209 kB]
Get:19 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [74.3 kB]
Get:20 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components [212 B]
Get:21 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components [208 B]
Get:22 http://archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [573 kB]
Get:23 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components [212 B]
Get:24 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 c-n-f Metadata [556 B]
Get:25 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages [31.8 kB]
Get:26 http://archive.ubuntu.com/ubuntu noble-updates/multiverse Translation-en [6348 B]
Get:27 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Get:28 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 c-n-f Metadata [496 B]
Get:29 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [7284 B]
Get:30 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [10.5 kB]
Get:31 http://archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components [216 B]
Get:32 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components [212 B]
Fetched 10.8 MB in 7s (1466 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
68 packages can be upgraded. Run 'apt list --upgradable' to see them.


   
- sudo apt install ufw -y
-  sudo apt install ufw -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  iptables libip4tc2 libip6tc2 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 nftables
Suggested packages:
  firewalld
The following NEW packages will be installed:
  iptables libip4tc2 libip6tc2 libnetfilter-conntrack3 libnfnetlink0 libnftables1 libnftnl11 nftables ufw
0 upgraded, 9 newly installed, 0 to remove and 68 not upgraded.
Need to get 1152 kB of archives.
After this operation, 5144 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libip4tc2 amd64 1.8.10-3ubuntu2 [23.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble/main amd64 libip6tc2 amd64 1.8.10-3ubuntu2 [23.7 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libnfnetlink0 amd64 1.0.2-2build1 [14.8 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 libnetfilter-conntrack3 amd64 1.0.9-6build1 [45.2 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble/main amd64 libnftnl11 amd64 1.2.6-2build1 [66.0 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble/main amd64 iptables amd64 1.8.10-3ubuntu2 [381 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble/main amd64 libnftables1 amd64 1.0.9-1build1 [358 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble/main amd64 nftables amd64 1.0.9-1build1 [69.8 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble/main amd64 ufw all 0.36.2-6 [169 kB]
Fetched 1152 kB in 3s (343 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libip4tc2:amd64.
(Reading database ... 43812 files and directories currently installed.)
Preparing to unpack .../0-libip4tc2_1.8.10-3ubuntu2_amd64.deb ...
Unpacking libip4tc2:amd64 (1.8.10-3ubuntu2) ...
Selecting previously unselected package libip6tc2:amd64.
Preparing to unpack .../1-libip6tc2_1.8.10-3ubuntu2_amd64.deb ...
Unpacking libip6tc2:amd64 (1.8.10-3ubuntu2) ...
Selecting previously unselected package libnfnetlink0:amd64.
Preparing to unpack .../2-libnfnetlink0_1.0.2-2build1_amd64.deb ...
Unpacking libnfnetlink0:amd64 (1.0.2-2build1) ...
Selecting previously unselected package libnetfilter-conntrack3:amd64.
Preparing to unpack .../3-libnetfilter-conntrack3_1.0.9-6build1_amd64.deb ...
Unpacking libnetfilter-conntrack3:amd64 (1.0.9-6build1) ...
Selecting previously unselected package libnftnl11:amd64.
Preparing to unpack .../4-libnftnl11_1.2.6-2build1_amd64.deb ...
Unpacking libnftnl11:amd64 (1.2.6-2build1) ...
Selecting previously unselected package iptables.
Preparing to unpack .../5-iptables_1.8.10-3ubuntu2_amd64.deb ...
Unpacking iptables (1.8.10-3ubuntu2) ...
Selecting previously unselected package libnftables1:amd64.
Preparing to unpack .../6-libnftables1_1.0.9-1build1_amd64.deb ...
Unpacking libnftables1:amd64 (1.0.9-1build1) ...
Selecting previously unselected package nftables.
Preparing to unpack .../7-nftables_1.0.9-1build1_amd64.deb ...
Unpacking nftables (1.0.9-1build1) ...
Selecting previously unselected package ufw.
Preparing to unpack .../8-ufw_0.36.2-6_all.deb ...
Unpacking ufw (0.36.2-6) ...
Setting up libip4tc2:amd64 (1.8.10-3ubuntu2) ...
Setting up libip6tc2:amd64 (1.8.10-3ubuntu2) ...
Setting up libnftnl11:amd64 (1.2.6-2build1) ...
Setting up libnfnetlink0:amd64 (1.0.2-2build1) ...
Setting up libnftables1:amd64 (1.0.9-1build1) ...
Setting up nftables (1.0.9-1build1) ...
Setting up libnetfilter-conntrack3:amd64 (1.0.9-6build1) ...
Setting up iptables (1.8.10-3ubuntu2) ...
update-alternatives: using /usr/sbin/iptables-legacy to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-legacy to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/iptables-nft to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-nft to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/arptables-nft to provide /usr/sbin/arptables (arptables) in auto mode
update-alternatives: using /usr/sbin/ebtables-nft to provide /usr/sbin/ebtables (ebtables) in auto mode
Setting up ufw (0.36.2-6) ...

Creating config file /etc/ufw/before.rules with new version

Creating config file /etc/ufw/before6.rules with new version

Creating config file /etc/ufw/after.rules with new version

Creating config file /etc/ufw/after6.rules with new version
Created symlink /etc/systemd/system/multi-user.target.wants/ufw.service → /usr/lib/systemd/system/ufw.service.
Processing triggers for libc-bin (2.39-0ubuntu8.6) ...
Processing triggers for rsyslog (8.2312.0-3ubuntu9.1) ...
Processing triggers for man-db (2.12.0-4build2) ...

- ufw --version
ufw 0.36.2
Copyright 2008-2023 Canonical Ltd.

### Firewall Status & Enable

-  sudo ufw status
Status: inactive

- sudo ufw enable
Firewall is active and enabled on system startup

- sudo ufw status
Status: active


### Allowing & Blocking Ports
- Common Commands
- sudo ufw allow 22
- sudo ufw deny 8080
- sudo ufw delete deny 8080
- sudo ufw allow 8080

### Start a Local Web Server
- python3 -m http.server 8080
- python3 -m http.server 8080
Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...
127.0.0.1 - - [28/Jan/2026 05:47:04] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [28/Jan/2026 05:47:35] "GET / HTTP/1.1" 200 -
curl http://localhost:8080

### Block the Port
- sudo ufw deny 8080

- Test Again
- curl http://localhost:8080


- Expected:

- Connection failed / Timed out

- Allow Again
- sudo ufw allow 8080


- Test:

- curl http://localhost:8080


- Expected:

HTML response returned

###  Viewing Firewall Rules
- sudo ufw status numbered
- [sudo] password for mantasha:
Status: active


### Issues Faced & Fixes
- Issue 1: ufw command not found

- Error:

- sudo: ufw: command not found


### Cause:
- Firewall package not installed.

### Fix:

- sudo apt update
- sudo apt install ufw


### Verified using:

- ufw --version

### Commands Summary
- sudo apt install ufw
- ufw --version
- sudo ufw status
- sudo ufw enable
- sudo ufw allow 22
- sudo ufw deny 8080
- sudo ufw delete deny 8080
- sudo ufw allow 8080
- sudo ufw status numbered
- python3 -m http.server 8080
- curl http://localhost:8080

## What I Learned Today

- How Linux firewalls work

- How to secure ports using UFW

- How to test blocked/allowed traffic

- How to troubleshoot firewall issues

- How real production servers are protected

### Outcome

- System secured using firewall rules.
- Practical experience gained in port security & network defense.

### ## Summary

- On Day 5, I learned how to secure a Linux system using a firewall and control network access at the port level.
-  I installed and configured UFW, enabled the firewall, and created rules to allow and block specific ports.
-  I also tested these rules in real time using a local web server and verified traffic using `curl`.

- This session helped me understand how production servers are protected from unauthorized access, how open ports increase security risks, and how to troubleshoot service connectivity issues caused by firewall restrictions.
- These skills are essential for Technical Support, Cloud Support, and Site Reliability roles where system security and network troubleshooting are critical.

