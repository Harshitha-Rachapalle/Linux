Process management means monitoring, controlling, and optimizing running programs (processes) on a Linux system. This includes starting/stopping, checking CPU/memory usage, and managing priority.

**What is a Process?**

A process is a **running instance**of a program.

> Every command you run creates a process.

> Each process gets a PID (Process ID).


### Viewing Processes

`ps aux` -> View all running processes  with cpu, memory utilization

`ps -ef' -> displays running processes

`ps aux | nl` -> gives the no.of lines

`ps aux | wc -l -> displays word count

### Monitoring System Processes

`top` -> Interactive process viewer. Real-time info sorted by CPU usage. Press q to quit.

`htop` — Enhanced version of top , Mouse support, Color-coded stats, Easy to kill/renice processes

`free -m` – Show memory usage

`vmstat` – Report system performance statistics

### Types of Processes

| Type       | Description                                     |
| ---------- | ----------------------------------------------- |
| Foreground | Requires user interaction (`nano`, `vim`, etc.)      |
| Background | Run in background (with `&` or `bg`)            |
| Daemon     | Background services (e.g., `sshd`, `cron`)      |
| Zombie     | Completed but still in process table (PPID = 1) |
| Orphan     | Parent exited, but process still runs           |


### Daemon Process Management

`systemctl list-units --type=service` – List all system daemons

`systemctl start service-name` – Start a daemon/service

`systemctl stop service-name` – Stop a daemon/service

`systemctl enable service-name` – Enable a service at startup


**How do you move a running job to the background?**

A: Press **Ctrl + Z** to suspend, then run **bg**.

**Q: How do you list all background jobs?**

A: Use the **jobs** command.

**Q: What’s the difference between & and bg?**

A: **&** runs a command immediately in the background; **bg** resumes a **stopped** job in the background.

### Managing Processes

`kill PID` – Terminate a process by PID

`pkill processname` – Terminate a process by name

`kill -9 PID` – Force kill a process

`pkill -9 processname` – Kill all instances of a process

`kill -STOP PID` – Stop a running process

`kill -CONT PID` – Resume a stopped process

`kill -15 PID` - terminates a process 

### priorities

**`nice`**

Processes have a priority (called niceness) ranging from **-20 (high priority) to 19 (low priority)**.

Starts with lower priority

Only **root can use negative nice values**

**`nice -n 10 command`**

**`renice`** :  Change Priority of Running Process

`renice -n 5 -p PID`









