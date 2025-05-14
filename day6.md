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
  ps ```
- To list all running processes:
```
ps -aux
```
- To check the number of processes:
  ``` ps aux | nl ```
- To get only the total number of processes:
``` ps aux | wc -l ```
###ps -aux vs ps -ef
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






