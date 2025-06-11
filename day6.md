# Process Management

A **process** is a running instance of any program. For example, a running Python application, a shell script, or a web server are all processes.

Processes utilize system resources like **CPU**, **memory**, etc. For instance, if a process is memory- or CPU-intensive and uses 90% of the CPU, only 10% is left for other processes, which may cause system performance issues.

As administrators, to manage this effectively, we perform several tasks:

1. View or check the processes
2. Kill, stop, or resume processes
3. Prioritize or deprioritize processes

---

## 1. View/Check Process

### Basic Commands

- To list some running processes:
  ```bash
  ps  ```
- To list all running processes:
```
ps -aux
```
- To check the number of processes:
  ``` ps aux | nl ```
- To get only the total number of processes:
``` ps aux | wc -l ```  
### ps -aux vs ps -ef
- Both commands list running processes.

-ps -aux displays:User (who initiated the process),PID (Process ID — a unique identifier),CPU and memory usage

- ps -ef does not show CPU and memory utilization by default.
### Kill a Process
- Sometimes a process might consume excessive system resources and needs to be terminated.
- Kill Commands:
- Kill a process using its PID:```kill <processid>```
- Example: Find and Kill a Java Process
- To find a Java process:``` ps aux | grep java ```
- To filter the actual Java process (excluding the grep process itself):```ps aux | grep java | grep -v grep  ```
- Use kill -9 <PID> to forcefully terminate a process if a regular kill doesn’t work
- to get the thread dumbs,ie logs of all the procersses and subprocess running inside a process :
  ``` kill -3 ```
### stop and resume a process:
-if u want to temporarily stop a process:
- get the process and pid ``` ps awx```
- so to stop the process ``` kill -STOP process id ```
- to restart the process ``` kill -CONT PID ```
### Prioritize and Depriritize :
- use the comand renice
  ### Stop and Resume a Process

- To temporarily stop a process:
  - Get the process and its PID using:
    ```
    ps awx
    ```
  - Stop the process using:
    ```
    kill -STOP <PID>
    ```
  - Restart the process using:
    ```
    kill -CONT <PID>
    ```

---

### Prioritize and Deprioritize a Process

- Use the `renice` command to adjust process priority:
  - Set priority:
    ```bash
    renice -n 10 -p <PID>
    ```
  - Priority range is from `-20` (highest priority) to `19` (lowest priority).
    - Example:
      ```bash
      renice -n -5 -p <PID>  # Higher priority
      renice -n 10 -p <PID>  # Lower priority
      ```
- Why prioritize?  
  By default, the CPU assumes a process using more time is more important. Managing priorities helps allocate resources more efficiently.

---

### Special Processes (Services)

- Services are background processes that start during system boot.
  - Examples: web servers (nginx, Apache), Java/Python apps, shell scripts
- To list running services:
  ```bash
  systemctl list-units --type=service
To stop a service:
```systemctl stop <servicename> ```
To start a stopped service:

```systemctl start <servicename>```
Can you convert a process to a service? Yes.
# Monitoring
### Monitor CPU, memory, and disk usage of processes:
Command	Description:
- top	Real-time CPU/memory usage, process info  
- htop	Enhanced visual version of top
- vmstat	System performance report
- free -m	Memory usage in MB (script-friendly)
- free -h	Memory usage in human-readable format
- nproc	Shows number of CPUs

### Disk and memory:

-df -h           : Disk usage per partition
-du -sh          :Folder disk usage (run inside the folder)
-Use grep, awk, sed on script-friendly outputs like free -m.
### Disk Space Utilization
View disk usage:
```df -h```
Check specific folder usage:

```du -sh```
Use these for quick checks. For advanced monitoring, integrate with:Prometheus,Grafana,Email or Slack notifications
# Disk Management
- When existing volume space is low, add a new volume:

- Use lsblk to view attached volumes:
```
lsblk
```
To list partition info:
```
fdisk -l
```
```Example:

Existing volume: /dev/xvda (8GB)

New volume: /dev/xvdf (10GB)
````

-Format the new volume:
```
mkfs -t ext4 /dev/xvdf
```
- Create a mount point:
 ```
mkdir -p /mnt/demovolume
```
- Create partitions (optional):
```gdisk /dev/xvdf
press: p → n → Enter → Enter → last sector → p → w
partprobe
```
- Verify with:
```
fdisk -l
```
-Format new partitions:

```
mkfs.ext4 /dev/xvdf1
```
- Mount the volume:
```
mount /dev/xvdf1 /mnt/demovolume
```
To verify:
```
blkid or lsblkor df-ht
```

-To make the mount permanent, edit /etc/fstab:

```
/dev/xvdf1   /mnt/demovolume   ext4   defaults   0 0
```
- To unmount a volume:
```
umount /mnt/demovolume
```







