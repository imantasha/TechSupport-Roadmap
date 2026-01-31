# In Day 7, we focus on one of the most important concepts for Technical Support Engineering:
## File permissions, ownership, and understanding access control in Linux.

## These concepts are frequently used in troubleshooting real-world production issues.

## Viewing Permissions – ls -l

- To view file details including permissions:
-  ls -l
total 16
-rw-r--r-- 1 mantasha mantasha    0 Jan 21 11:11 Hello
drwxr-xr-x 3 mantasha mantasha 4096 Jan 24 12:47 TechSupport-Roadmap
drwxr-xr-x 2 mantasha mantasha 4096 Jan 21 10:57 f2
-rwxr-xr-x 1 mantasha mantasha  173 Jan 21 11:21 file.txt
-rwxr-xr-x 1 mantasha mantasha    0 Jan 21 09:51 file1.sh
drwxr-xr-x 2 mantasha mantasha 4096 Jan 21 10:57 folder


- Breakdown

-	File type (- = file, d = directory)
- rw-	Owner permissions
- r--	Group permissions
- r--	Others permissions
- mantasha	Owner
- mantasha	Group

## Permission Legend

- r = read

- w = write

- x = execute

---

## Changing Permissions – chmod
- Add Execute Permission
- chmod +x script.sh
- (No output means success.)

---

## Changing Ownership – chown
- Change Owner of a File
- sudo chown mantasha file.txt


Output:

-rw-r--r-- 1 mantasha mantasha 900 Jan 21 file.txt

---

## Changing Ownership – chown
- Change Owner of a File
- sudo chown mantasha file.txt

- Output:

- -rw-r--r-- 1 mantasha mantasha 900 Jan 21 file.txt

---

## Viewing Logged-in Users – who / w
- whoami


Output:

mantasha

## w
- w
- Output:

-   07:54:15 up 2 min,  1 user,  load average: 0.07, 0.07, 0.03
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU  WHAT
mantasha pts/1    -                07:52    2:06   0.07s  0.05s -bash

---

## Switching to Root User – sudo -i
-
[sudo] password for mantasha:
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.6.87.2-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Sat Jan 31 08:15:32 UTC 2026

  System load:  0.15                Processes:             37
  Usage of /:   0.2% of 1006.85GB   Users logged in:       1
  Memory usage: 9%                  IPv4 address for eth0: 192.168.193.240
  Swap usage:   0%

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

This message is shown once a day. To disable it please create the
/root/.hushlogin file.

## To exit root:

- exit

- Output
- logout


---
## Common Permission Issues & Fixes
- Issue: Permission Denied While Running Script
bash: ./backup.sh: Permission denied

- Fix:
chmod +x backup.sh

- Issue: Cannot Edit File — Not Owner
permission denied: config.txt

- Fix:
sudo chown mantasha config.txt

- Issue: Folder Not Accessible
cd: permission denied: /var/log/app

- Fix:
sudo chmod 755 /var/log/app



---

## Day 7 Summary

- Learned how to read file permissions (rwx)

- Understood owner, group, and others

- Practiced modifying permissions with chmod

- Learned ownership changes using chown

- Checked user identity using whoami

- Viewed logged-in users using who and w

- Used safe privilege switching with sudo -i

- Fixed common permission issues

---
