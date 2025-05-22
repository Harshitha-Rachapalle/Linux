##  System Logs (/var/log)

Linux stores logs primarily in the **/var/log/** directory. These are essential for troubleshooting.

| File                                     | Purpose                              |
| ---------------------------------------- | ------------------------------------ |
| `/var/log/syslog` or `/var/log/messages` | General system activity logs         |
| `/var/log/auth.log`                      | Authentication events (logins, sudo) |
| `/var/log/dmesg`                         | Kernel ring buffer (hardware logs)   |
| `/var/log/kern.log`                      | Kernel logs                          |
| `/var/log/boot.log`                      | Boot process logs                    |
| `/var/log/cron`                          | Cron job logs                        |
| `/var/log/secure`                        | Security and auth (Red Hat systems)  |
| `/var/log/httpd/` or `/var/log/nginx/`   | Web server logs                      |


 **Example:** **View Real-Time Log Updates**
```
tail -f /var/log/syslog
```
**How are logs managed on systemd-based systems?**

A: With **journalctl** (reads from the journal log database)

```
journalctl -xe                         # View recent system errors
journalctl -u nginx                   # Logs for nginx service
journalctl --since "10 minutes ago"  # Logs in time range
```

## logrotate
It prevents disk space exhaustion by

> Rotate logs (rename and start fresh)

> Compress old ones

> Retain them for a set number of days

> Keep disk space under control


### How Logrotate Works (Step-by-Step)

Logrotate reads configuration rules from `/etc/logrotate.conf` or individual config files inside `/etc/logrotate.d/`.

**Example Logrotate Configuration**

manage Nginx logs, ensuring they are rotated daily and stored for 7 days before deletion

```
/var/log/nginx/*.log {
    daily          # Rotate logs every day
    rotate 7       # Keep only the last 7 rotated logs
    compress       # Compress old logs to save space
    missingok      # Ignore errors if log files are missing
    notifempty     # Skip rotation if log file is empty
    create 0640 root root  # Create new logs with proper permissions
    postrotate
        systemctl reload nginx  # Restart Nginx after log rotation
    endscript
}
```

## System Monitoring Tools & Their Functions

✅ **top** → Real-Time System Monitoring

> Displays CPU & Memory usage, running processes, and system load.

> Press q to exit.

> Ideal for quick snapshots of system performance.

✅ **htop** → Interactive Process Viewer

> More user-friendly than top, with colorful graphs.

> Allows process management (kill, renice) directly in the interface.

> Navigate using arrow keys.

> Recommended when troubleshooting high CPU or RAM usage!

✅ **vmstat** → Memory & System Performance Stats

`vmstat 5 10`

Monitors system performance at intervals.

5 → Update every 5 seconds.

10 → Run 10 updates, then stop.

> Useful for diagnosing memory bottlenecks and swap usage.


✅ **iostat** → Disk & I/O Monitoring

`iostat -x 5`

Displays disk activity & I/O performance.

-x → Show extended stats (useful for bottleneck analysis).

5 → Updates every 5 seconds.

✅ Helps identify slow disks or overloaded I/O operations.


 
