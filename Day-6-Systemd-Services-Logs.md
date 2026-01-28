# Day 6 – systemd, Service Management, Process Monitoring & Log Analysis

## Objective

Learn how Linux manages background services, how to install and troubleshoot real applications, monitor running processes, analyze logs, and handle common production issues like service downtime and package manager locks.

---

## systemd – Theory

`systemd` is the default service manager in modern Linux systems. It is responsible for:

- Starting services at boot
- Stopping and restarting services
- Monitoring service health
- Managing dependencies
- Collecting logs using the system journal

A service is a background program such as `ssh`, `apache2`, or `docker`.

Important service states:

- **active (running)** – service is working
- **inactive** – service is stopped
- **failed** – service crashed

The main command used to manage services is:

```bash
systemctl
Check SSH service status
systemctl status ssh
```
- systemctl status ssh
○ ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: inactive (dead) since Wed 2026-01-28 06:15:58 UTC; 20s ago
   Duration: 40.189s
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1969 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
    Process: 1970 ExecStart=/usr/sbin/sshd -D $SSHD_OPTS (code=exited, status=0/SUCCESS)
   Main PID: 1970 (code=exited, status=0/SUCCESS)
        CPU: 46ms

Jan 28 06:15:18 MantashaIdrisi systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Jan 28 06:15:18 MantashaIdrisi sshd[1970]: Server listening on 0.0.0.0 port 22.
Jan 28 06:15:18 MantashaIdrisi sshd[1970]: Server listening on :: port 22.
Jan 28 06:15:18 MantashaIdrisi systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Jan 28 06:15:58 MantashaIdrisi sshd[1970]: Received signal 15; terminating.
Jan 28 06:15:58 MantashaIdrisi systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Jan 28 06:15:58 MantashaIdrisi systemd[1]: ssh.service: Deactivated successfully.
Jan 28 06:15:58 MantashaIdrisi systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.

---

- sudo systemctl restart ssh
- sudo systemctl stop ssh
- sudo systemctl start ssh

-  ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: active (running) since Wed 2026-01-28 06:16:35 UTC; 8s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1997 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 1998 (sshd)
      Tasks: 1 (limit: 4615)
     Memory: 1.2M (peak: 1.8M)
        CPU: 27ms
     CGroup: /system.slice/ssh.service
             └─1998 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Jan 28 06:16:35 MantashaIdrisi systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Jan 28 06:16:35 MantashaIdrisi sshd[1998]: Server listening on 0.0.0.0 port 22.
Jan 28 06:16:35 MantashaIdrisi sshd[1998]: Server listening on :: port 22.
Jan 28 06:16:35 MantashaIdrisi systemd[1]: Started ssh.service - OpenBSD Secure Shell server.

---

### Enable service at boot
- sudo systemctl enable ssh
 sudo systemctl enable ssh
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable ssh
Created symlink /etc/systemd/system/sshd.service → /usr/lib/systemd/system/ssh.service.
Created symlink /etc/systemd/system/multi-user.target.wants/ssh.service → /usr/lib/systemd/system/ssh.service.
### Disable service at boot
- sudo systemctl disable ssh
- ~$ sudo systemctl disable ssh
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install disable ssh
Removed "/etc/systemd/system/sshd.service".
Removed "/etc/systemd/system/multi-user.target.wants/ssh.service".
Disabling 'ssh.service', but its triggering units are still active:
ssh.socket

--- 

### Installing and Running Apache Web Server
- Install Apache
-  sudo apt install apache2

-  sudo apt install apache2 -y
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2162 (unattended-upgr)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  apache2-bin apache2-data apache2-utils libapr1t64 libaprutil1-dbd-sqlite3 libaprutil1-ldap libaprutil1t64 liblua5.4-0 ssl-cert
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom www-browser
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libapr1t64 libaprutil1-dbd-sqlite3 libaprutil1-ldap libaprutil1t64 liblua5.4-0 ssl-cert
0 upgraded, 10 newly installed, 0 to remove and 59 not upgraded.
Need to get 2090 kB of archives.
After this operation, 8113 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libapr1t64 amd64 1.7.2-3.1ubuntu0.1 [108 kB]
Get:2 http://archive.ubuntu.com/ubuntu noble/main amd64 libaprutil1t64 amd64 1.6.3-1.1ubuntu7 [91.9 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/main amd64 libaprutil1-dbd-sqlite3 amd64 1.6.3-1.1ubuntu7 [11.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 libaprutil1-ldap amd64 1.6.3-1.1ubuntu7 [9116 B]
Get:5 http://archive.ubuntu.com/ubuntu noble/main amd64 liblua5.4-0 amd64 5.4.6-3build2 [166 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apache2-bin amd64 2.4.58-1ubuntu8.10 [1334 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apache2-data all 2.4.58-1ubuntu8.10 [163 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apache2-utils amd64 2.4.58-1ubuntu8.10 [98.1 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 apache2 amd64 2.4.58-1ubuntu8.10 [90.2 kB]
Get:10 http://archive.ubuntu.com/ubuntu noble/main amd64 ssl-cert all 1.1.2ubuntu1 [17.8 kB]
Fetched 2090 kB in 19s (109 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libapr1t64:amd64.
(Reading database ... 44185 files and directories currently installed.)
Preparing to unpack .../0-libapr1t64_1.7.2-3.1ubuntu0.1_amd64.deb ...
Unpacking libapr1t64:amd64 (1.7.2-3.1ubuntu0.1) ...
Selecting previously unselected package libaprutil1t64:amd64.
Preparing to unpack .../1-libaprutil1t64_1.6.3-1.1ubuntu7_amd64.deb ...
Unpacking libaprutil1t64:amd64 (1.6.3-1.1ubuntu7) ...
Selecting previously unselected package libaprutil1-dbd-sqlite3:amd64.
Preparing to unpack .../2-libaprutil1-dbd-sqlite3_1.6.3-1.1ubuntu7_amd64.deb ...
Unpacking libaprutil1-dbd-sqlite3:amd64 (1.6.3-1.1ubuntu7) ...
Selecting previously unselected package libaprutil1-ldap:amd64.
Preparing to unpack .../3-libaprutil1-ldap_1.6.3-1.1ubuntu7_amd64.deb ...
Unpacking libaprutil1-ldap:amd64 (1.6.3-1.1ubuntu7) ...
Selecting previously unselected package liblua5.4-0:amd64.
Preparing to unpack .../4-liblua5.4-0_5.4.6-3build2_amd64.deb ...
Unpacking liblua5.4-0:amd64 (5.4.6-3build2) ...
Selecting previously unselected package apache2-bin.
Preparing to unpack .../5-apache2-bin_2.4.58-1ubuntu8.10_amd64.deb ...
Unpacking apache2-bin (2.4.58-1ubuntu8.10) ...
Selecting previously unselected package apache2-data.
Preparing to unpack .../6-apache2-data_2.4.58-1ubuntu8.10_all.deb ...
Unpacking apache2-data (2.4.58-1ubuntu8.10) ...
Selecting previously unselected package apache2-utils.
Preparing to unpack .../7-apache2-utils_2.4.58-1ubuntu8.10_amd64.deb ...
Unpacking apache2-utils (2.4.58-1ubuntu8.10) ...
Selecting previously unselected package apache2.
Preparing to unpack .../8-apache2_2.4.58-1ubuntu8.10_amd64.deb ...
Unpacking apache2 (2.4.58-1ubuntu8.10) ...
Selecting previously unselected package ssl-cert.
Preparing to unpack .../9-ssl-cert_1.1.2ubuntu1_all.deb ...
Unpacking ssl-cert (1.1.2ubuntu1) ...
Setting up ssl-cert (1.1.2ubuntu1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/ssl-cert.service → /usr/lib/systemd/system/ssl-cert.service.
Setting up libapr1t64:amd64 (1.7.2-3.1ubuntu0.1) ...
Setting up liblua5.4-0:amd64 (5.4.6-3build2) ...
Setting up apache2-data (2.4.58-1ubuntu8.10) ...
Setting up libaprutil1t64:amd64 (1.6.3-1.1ubuntu7) ...
Setting up libaprutil1-ldap:amd64 (1.6.3-1.1ubuntu7) ...
Setting up libaprutil1-dbd-sqlite3:amd64 (1.6.3-1.1ubuntu7) ...
Setting up apache2-utils (2.4.58-1ubuntu8.10) ...
Setting up apache2-bin (2.4.58-1ubuntu8.10) ...
Setting up apache2 (2.4.58-1ubuntu8.10) ...
Enabling module mpm_event.
Enabling module authz_core.
Enabling module authz_host.
Enabling module authn_core.
Enabling module auth_basic.
Enabling module access_compat.
Enabling module authn_file.
Enabling module authz_user.
Enabling module alias.
Enabling module dir.
Enabling module autoindex.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module filter.
Enabling module deflate.
Enabling module status.
Enabling module reqtimeout.
Enabling conf charset.
Enabling conf localized-error-pages.
Enabling conf other-vhosts-access-log.
Enabling conf security.
Enabling conf serve-cgi-bin.
Enabling site 000-default.
Created symlink /etc/systemd/system/multi-user.target.wants/apache2.service → /usr/lib/systemd/system/apache2.service.
Created symlink /etc/systemd/system/multi-user.target.wants/apache-htcacheclean.service → /usr/lib/systemd/system/apache-htcacheclean.service.
Processing triggers for ufw (0.36.2-6) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.6) ... 

---

### Issues Faced & Fixes
- Issue 1 – dpkg Lock / Package Database Error

- Error:

- E: Could not get lock /var/lib/dpkg/lock-frontend
- dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'


- Cause:

- Another package process (like unattended-upgrades) was already running.

- The package database became locked or inconsistent.

- Fix:
```
sudo dpkg --configure -a
sudo apt --fix-broken install
sudo apt install apache2

```
- Verification:

- systemctl status apache2


- Output:

- Active: active (running)

---
### Summary 

- On Day 6, I learned how Linux manages background services using systemd and how real-world production services are installed, monitored, and recovered from failures.

- I practiced managing services using systemctl, including starting, stopping, restarting, enabling, disabling, and checking service status. I also installed and tested the Apache web server, simulated a real service outage, and restored it like a support engineer.

- Additionally, I learned how to monitor system processes using ps and top, analyze service logs using journalctl, and fix package installation issues caused by dpkg locks and broken dependencies.

- This day provided hands-on experience with real system administration tasks that are critical for Technical Support Engineers, Cloud Support roles, and SRE positions, where uptime, troubleshooting, and system reliability are essential.
