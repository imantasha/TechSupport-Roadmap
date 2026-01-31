Day 8 – Linux Processes & System Monitoring (Technical Support Engineering)

Welcome to Day 8 of  Linux learning journey!
Today we dive into one of the most critical concepts for real-world troubleshooting:
process management and monitoring system performance.

 What we Will Learn

What Linux processes are

Checking running processes

Understanding system metrics (CPU, RAM, load average)

Foreground vs background jobs

Killing processes

Using ps, top, htop, kill, free, df, du

Troubleshooting common high-CPU or memory issues

 What is a Process?

A process is any running program in Linux.

Each process has:

PID → Process ID

PPID → Parent Process ID

USER → Who started it

STAT → Process state

COMMAND → Program being executed

 Viewing Running Processes
 1. List All Processes
ps aux


Example Output:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
mantasha  1223  0.0  0.1  12340  2100 pts/1    Ss   07:50   0:00 bash
root      1121  0.2  1.0 234000 25000 ?        Sl   07:49   0:01 systemd

 2. Tree View of Processes

Shows the parent-child hierarchy:

ps -ef --forest

 Real-Time System Monitoring
 top – Live View of Processes
top


Displays:

CPU usage

Memory usage

Load average

Running processes

 htop – Colorful, Interactive Monitor

Install:

sudo apt install htop


Run:

htop


Features:

Scrollable

Searchable

Easy process killing

 Foreground & Background Jobs
 Run a program in background:
./script.sh &

 List background jobs:
jobs

 Bring job to foreground:
fg %1

 Send job to background:

Press:

Ctrl + Z


Then:

bg

 Killing or Stopping Processes
Kill process by PID:
kill 1234

Force kill:
kill -9 1234

Kill by name:
pkill firefox

Kill all processes with same name:
killall python

 Checking System Resources
 Memory Usage:
free -h

 Disk Space:
df -h

 Folder Size:
du -sh /var/log

 CPU Info:
lscpu

 Common Process Issues & Fixes
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

 Day 8 Summary

Today we learned:

 What Linux processes are

 Viewing processes (ps, top, htop)

 How to run, pause, and background jobs

 Killing & managing processes

✔ Monitoring CPU, memory, disk usage

✔ Troubleshooting slow or unresponsive systems
