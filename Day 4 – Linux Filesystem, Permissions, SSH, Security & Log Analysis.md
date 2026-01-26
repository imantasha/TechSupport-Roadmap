# Day 4 – Linux Filesystem, Permissions, SSH, Security & Log Analysis

## Objective
To gain real-world Linux system administration and support engineer skills by understanding:

- Linux filesystem structure
- File permissions & ownership
- SSH remote access
- sudo & basic security
- System log analysis
- Hands-on practice

---

## Part 1 – Linux Filesystem (Theory + Practical)

Linux follows a single-root directory structure starting from `/`.

### Important Directories

| Directory | Purpose |
|----------|----------|
| / | Root directory |
| /home | User files |
| /etc | Configuration files |
| /bin | Essential system commands |
| /sbin | System admin commands |
| /var | Logs & variable data |
| /tmp | Temporary files |
| /usr | Installed software |
| /opt | Optional software |
| /proc | Kernel info |
| /dev | Device files |

---

### Commands Practiced

```bash
pwd
```
### $ pwd
/home/mantasha

$ ls -lah
total 64K
drwxr-x--- 7 mantasha mantasha 4.0K Jan 25 10:46 .
drwxr-xr-x 3 root     root     4.0K Jan 21 09:04 ..
-rw------- 1 mantasha mantasha 1.8K Jan 25 13:40 .bash_history
-rw-r--r-- 1 mantasha mantasha  220 Jan 21 09:04 .bash_logout
-rw-r--r-- 1 mantasha mantasha 3.7K Jan 21 09:04 .bashrc
drwx------ 2 mantasha mantasha 4.0K Jan 21 09:05 .cache
drwx------ 4 mantasha mantasha 4.0K Jan 21 11:26 .config
-rw------- 1 mantasha mantasha   70 Jan 24 12:56 .git-credentials
-rw-r--r-- 1 mantasha mantasha   29 Jan 24 12:56 .gitconfig
-rw------- 1 mantasha mantasha   20 Jan 25 10:46 .lesshst
-rw-rw-r-- 1 mantasha mantasha    0 Jan 26 10:42 .motd_shown
-rw-r--r-- 1 mantasha mantasha  807 Jan 21 09:04 .profile
-rw-r--r-- 1 mantasha mantasha    0 Jan 21 09:48 .sudo_as_admin_successful
-rw-r--r-- 1 mantasha mantasha 1.9K Jan 24 12:13 .wsl-config
-rw-r--r-- 1 mantasha mantasha    0 Jan 21 11:11 Hello
drwxr-xr-x 3 mantasha mantasha 4.0K Jan 24 12:47 TechSupport-Roadmap
drwxr-xr-x 2 mantasha mantasha 4.0K Jan 21 10:57 f2
-rw-r--r-- 1 mantasha mantasha  173 Jan 21 11:21 file.txt
-rwxr-xr-x 1 mantasha mantasha    0 Jan 21 09:51 file1.sh
drwxr-xr-x 2 mantasha mantasha 4.0K Jan 21 10:57 folder

## Linux permissions format:

- -rwxr-xr--

- rwx	Owner
- r-x	Group
- r--	Others
## Permission Numbers
## Number	    Permission
- 4	            Read
- 2            	Write
- 1	            Execute

### Example:

- 755 = rwx r-x r-x

### Commands Practiced
- ls -l
- chmod 755 file.txt
- chmod 600 file.txt
- sudo chown mantasha file.txt

###  Output
- -rwxr-xr-x 1 mantasha mantasha 0 file.txt

### Why Permissions Matter in Production

- Prevent unauthorized access to sensitive files
- Avoid "Permission denied" application errors
- Protect SSH keys and config files
- Secure logs and databases
- Stop malware from modifying system files


--- 
### SSH (Secure Shell)

- SSH allows secure remote access to servers.

- Default port: 22

- Used in cloud servers (AWS, GCP, Azure)

### Commands Practiced
- systemctl status ssh
- ssh user@server_ip

###  Output
- Active: active (running)
- Server listening on 0.0.0.0 port 22

### SSH Key Authentication
- ssh-keygen
- ssh-copy-id user@server_ip



## sudo (Super User Do)

sudo allows normal users to execute administrative commands securely.

Examples:

sudo apt update
sudo systemctl restart ssh
- Why sudo is important:
- Avoids logging in as root
- Keeps audit logs
- Limits damage from mistakes


## Log Analysis

Important directory:

- /var/log
- /var/log
-bash: /var/log: Is a directory

Important files:
- syslog → system events
- auth.log → SSH & login attempts
- dpkg.log → package installation
- kern.log → kernel messages

Commands used:

- tail -f /var/log/syslog
-  tail -f /var/log/syslog
2026-01-26T11:07:00.113215+00:00 MantashaIdrisi wsl-pro-service[206]: #033[36mINFO#033[0m Daemon: connecting to Windows Agent
2026-01-26T11:07:00.114167+00:00 MantashaIdrisi wsl-pro-service[206]: #033[37mDEBUG#033[0m Updated systemd status to "Connecting"
2026-01-26T11:07:00.122121+00:00 MantashaIdrisi wsl-pro-service[206]: #033[33mWARNING#033[0m Daemon: could not connect to Windows Agent: could not get address: could not read agent port file "/mnt/c/Users/DEV/.ubuntupro/.address": open /mnt/c/Users/DEV/.ubuntupro/.address: no such file or directory
2026-01-26T11:07:00.122431+00:00 MantashaIdrisi wsl-pro-service[206]: #033[36mINFO#033[0m Reconnecting to Windows host in 60 seconds
2026-01-26T11:07:00.122709+00:00 MantashaIdrisi wsl-pro-service[206]: #033[37mDEBUG#033[0m Updated systemd status to "Not connected: waiting to retry"
2026-01-26T11:08:00.183200+00:00 MantashaIdrisi wsl-pro-service[206]: #033[36mINFO#033[0m Daemon: connecting to Windows Agent
2026-01-26T11:08:00.219260+00:00 MantashaIdrisi wsl-pro-service[206]: #033[37mDEBUG#033[0m Updated systemd status to "Connecting"
2026-01-26T11:08:00.219472+00:00 MantashaIdrisi wsl-pro-service[206]: #033[33mWARNING#033[0m Daemon: could not connect to Windows Agent: could not get address: could not read agent port file "/mnt/c/Users/DEV/.ubuntupro/.address": open /mnt/c/Users/DEV/.ubuntupro/.address: no such file or directory
2026-01-26T11:08:00.219556+00:00 MantashaIdrisi wsl-pro-service[206]: #033[36mINFO#033[0m Reconnecting to Windows host in 60 seconds
2026-01-26T11:08:00.219645+00:00 MantashaIdrisi wsl-pro-service[206]: #033[37mDEBUG#033[0m Updated systemd status to "Not connected: waiting to retry"
^C



grep error /var/log/syslog
journalctl -u ssh


 ## output  
 -  journalctl -u ssh
Jan 25 10:46:18 MantashaIdrisi systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Jan 25 10:46:18 MantashaIdrisi sshd[1766]: Server listening on 0.0.0.0 port 22.
Jan 25 10:46:18 MantashaIdrisi sshd[1766]: Server listening on :: port 22.
Jan 25 10:46:18 MantashaIdrisi systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Jan 25 13:40:24 MantashaIdrisi systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Jan 25 13:40:24 MantashaIdrisi sshd[1766]: Received signal 15; terminating.
Jan 25 13:40:24 MantashaIdrisi systemd[1]: ssh.service: Deactivated successfully.
Jan 25 13:40:24 MantashaIdrisi systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.


## Issues Faced & Fixes

- Issue:
- dpkg was interrupted and package database became inconsistent.

- Fix:

- sudo dpkg --configure -a
- sudo apt --fix-broken install




## Git Commands Used

git status
git add .
git commit -m "Day 4: Filesystem, permissions, SSH & logs"
git push


### Summary – What I Learned

- Linux filesystem hierarchy

- File permissions & ownership management

- Secure remote access using SSH

- System service control

- Advanced log analysis

- Practical troubleshooting techniques
