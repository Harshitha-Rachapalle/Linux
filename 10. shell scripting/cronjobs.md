## What is cron?

✅ Cron is a **time-based job scheduler** in Unix/Linux.

✅ Runs commands or scripts automatically at predefined times.

✅ Perfect for backups, system updates, log cleanup, and scheduled tasks.

## 🔹 What is crontab?

✅ Crontab (short for cron table) is where **cron jobs are stored and managed**.

✅ Users edit crontab to define their scheduled tasks.

✅ Each cron job follows a precise time format.

**View Existing Cron Jobs**
```
crontab -l
```

**Edit Your Cron Jobs**

```
crontab -e
```

Opens the crontab editor, where you can define scheduled tasks.

**Deletes all scheduled tasks**

```
crontab -r
```

## crontab format
 
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of week (0 - 6) (Sunday to Saturday)
# │ │ │ │ │
# │ │ │ │ │
# * * * * *  command to run


## Real Use Case – Log Cleanup
```
sudo nano /usr/local/bin/clean_old_logs.sh
```

```
#!/bin/bash
find /var/log/legacy/ -type f -name "*.log" -mtime +7 -exec rm {} \;
```

Make it executable:
```
chmod +x /usr/local/bin/clean_old_logs.sh
```

Then add to root’s crontab:
```
sudo crontab -e
```
```
0 2 * * * /usr/local/bin/clean_old_logs.sh
```

Every day at 2 AM, logs older than 7 days are deleted.

**Q: How do you log output from cron?**

* * * * * /path/to/script.sh >> /var/log/myscript.log 2>&1
       

## What is at? (One-Time Scheduled Execution)

✅ Schedules a command to run at a specific future time.

✅ Executes only once (unlike cron, which repeats jobs).

🔹 Example: Run a Script at 6 PM
```
at 18:00
```

Then type:
```
echo "Running maintenance script..." >> ~/maint.log
```
Press Ctrl + D to save the job.

✅ The script will execute exactly at 6 PM.

🔹 View Scheduled Jobs
```
atq
```
✅ Lists all pending at jobs.

🔹 Remove a Scheduled Job
```
atrm <job_id>
```
✅ Cancels a specific scheduled task.

 ## What is batch? (Run When System Load is Low)
 
✅ Executes jobs when system load is below a defined threshold.

✅ Ideal for resource-heavy tasks that should run only when the system is idle.

🔹 Example: Schedule a Backup When System Load is Low
```
batch
```

Then type:
```
tar -czf /backup/data.tar.gz ~/important_files
```
Press Ctrl + D to save.

✅ The backup job runs automatically when the system load drops.

## How These Help in Real Life
✅ **at** ensures time-sensitive scripts run exactly when needed.

✅ **batch** prevents heavy operations from slowing down active users.

✅ Automates system maintenance, updates, and backups without intervention.
