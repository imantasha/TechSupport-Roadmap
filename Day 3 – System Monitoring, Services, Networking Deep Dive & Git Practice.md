# Day 3 – System Monitoring, Services, Networking Deep Dive & Git Practice

## Objective
Build real-world Technical Support / Cloud Support skills by learning how to:

- Inspect open ports and services
- Run and test applications
- Monitor CPU, memory, disk, and system load
- Troubleshoot networking issues
- Manage Linux services
- Practice Git workflow

---

## Part 1 – Ports & Services

### Commands Practiced
- ss -tulnp
- netstat -tulnp
- python3 -m http.server 8080
- curl http://localhost:8080

### Purpose
- Identify which services are running
- Verify application ports
- Test local web servers

### Example Output (ss -tulnp)
### ss -tulnp
Netid          State           Recv-Q          Send-Q                    Local Address:Port                     Peer Address:Port          Process
udp            UNCONN          0               0                            127.0.0.54:53                            0.0.0.0:*
udp            UNCONN          0               0                         127.0.0.53%lo:53                            0.0.0.0:*
udp            UNCONN          0               0                        10.255.255.254:53                            0.0.0.0:*
udp            UNCONN          0               0                             127.0.0.1:323                           0.0.0.0:*
udp            UNCONN          0               0                                 [::1]:323                              [::]:*
tcp            LISTEN          0               4096                      127.0.0.53%lo:53                            0.0.0.0:*
tcp            LISTEN          0               1000                     10.255.255.254:53                            0.0.0.0:*
tcp            LISTEN          0               4096                         127.0.0.54:53                            0.0.0.0:*


### Key Learnings

Key Learnings
- LISTEN state means a service is actively accepting connections
- Port 22 → SSH service
- Port 8080 → Application/web server
- ss is faster and preferred over netstat on modern Linux

---   

### Part 2 – Service Management (systemctl)
Commands Practiced

- systemctl status ssh

- sudo systemctl start ssh

- sudo systemctl stop ssh

- sudo systemctl restart ssh

### Example Output
###  sudo systemctl start ssh
mantasha@MantashaIdrisi:~$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: active (running) since Sun 2026-01-25 10:46:18 UTC; 7s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1765 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 1766 (sshd)
      Tasks: 1 (limit: 4615)
     Memory: 1.2M (peak: 1.6M)
        CPU: 46ms
     CGroup: /system.slice/ssh.service
             └─1766 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Jan 25 10:46:18 MantashaIdrisi systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Jan 25 10:46:18 MantashaIdrisi sshd[1766]: Server listening on 0.0.0.0 port 22.
Jan 25 10:46:18 MantashaIdrisi sshd[1766]: Server listening on :: port 22.
Jan 25 10:46:18 MantashaIdrisi systemd[1]: Started ssh.service - OpenBSD Secure Shell server.

## Key Learnings

- Services must be running to accept connections

- Restarting services fixes many production issues


--- 

## Part 3 – System Monitoring
- Commands Practiced

### top

### free -h

### df -h

### uptime

### vmstat 1

### iostat

## Purpose
## Command	Usage
-top	Live CPU & memory
-free -h	RAM usage
-df -h	Disk usage
-uptime	Load average
-vmstat	CPU & memory stats
-iostat	Disk performance
-Example Output (free -h)
Mem: 3.8G total, 2.1G used, 1.7G free

## Key Learnings

-High CPU → performance issues

- Low memory → app crashes

- High disk usage → server failures

 - Load average > CPU cores → overload

## Part 4 – Networking Troubleshooting
## Commands Practiced

### ip a

### ip route

### ping 8.8.8.8

### ping google.com

### nslookup google.com

### curl https://google.com

### Troubleshooting Flow Used

### Check IP address → ip a

### Check gateway → ip route

### Check internet → ping 8.8.8.8

### Check DNS → ping google.com / nslookup

### Check application → curl

## Conclusion

Network connectivity and DNS resolution verified successfully.



## ISSUES FACED AND FIXES 
### Issue: Package installation failed with error: "dpkg was interrupted, package database is inconsistent."

### Fix:
Reconfigured pending packages using:

sudo dpkg --configure -a

Resolved broken dependencies using:

sudo apt --fix-broken install

After fixing the package state, installation worked normally.




## Summary

This day strengthened my foundation for L1/L2 Technical Support and Cloud Support roles by giving me hands-on experience with:

- Linux service management
- System performance monitoring
- Network troubleshooting methodology
- Real-world package management issues
- Git-based workflow

