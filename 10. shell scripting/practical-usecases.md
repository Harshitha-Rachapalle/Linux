## 1. Disk Usage Alert Script

**This script:**

Defines a threshold for disk usage.

Gets the current disk usage percentage.

Compares it with the threshold (80%).

Alerts the user if disk usage is too high.

```
#!/bin/bash

threshold=80

usage=$(df -h / | grep '/' | awk '{print $5}' | sed 's/%//')

if [ "$usage" -gt "$threshold" ]; then

  echo "Disk usage is above $threshold%! ($usage%)"

  # Optional: send email or alert to Slack

else

  echo "Disk usage is OK: $usage%"

fi
```

**explanation:**

**`usage=$(df -h / | grep '/' | awk '{print $5}' | sed 's/%//')`**

This command retrieves the **current disk usage percentage.**

1.**`df -h /`** → Shows disk space usage for the root filesystem (/).

2.**`grep '/'`** → Filters the output to **find the line** that **contains /** (root disk).

**ex output:**

/dev/sda1      50G  42G  8G  85% /

3.**`awk '{print $5}'`** → Extracts the **5th column**, which contains the **disk usage percentage** (85%).

Awk treats space-separated words as columns ($1, $2, $3...).

Column 5 is the disk usage percentage (85%).

4.**`sed 's/%//'`** → **Removes the % symbol** so we can compare it as a numeric value.

sed → Stream editor.

s/%// → Replace % with nothing (removes % from 85%, leaving 85).**here s means substitute**

**🔹 Example Run**

If disk usage is 85%, the script prints:

Disk usage is above 80%! (85%)

If disk usage is 75%, it prints:

Disk usage is OK: 75%

**How This Helps in Real Life**

✅**Prevents server crashes** due to full disk

✅ **Warns** before disk issues escalate

✅ Helps system admins **automate monitoring**


## 2. Service Health Check Script

```
#!/bin/bash

services=("nginx" "docker" "sshd")

for service in "${services[@]}"; do

  if systemctl is-active --quiet $service; then

    echo "$service is running ✅"

  else

    echo "$service is NOT running ❌"

    systemctl restart $service

  fi

done
```

**Explanation:**

`services=("nginx" "docker" "sshd")`

**Defines an array** containing three services:

nginx → Web server.

docker → Container management.

sshd → Remote login (SSH).

`for service in "${services[@]}"; do`

**Loops through each service** in the array.

`if systemctl is-active --quiet $service; then`

**Checks if the service is running** using systemctl:

`is-active` → Checks if the service is currently running.

`--quiet` → Suppresses unnecessary output.

If the service is running, it moves to the next step.

Prints a confirmation message

`  else
    echo "$service is NOT running ❌"
    systemctl restart $service
  fi
`
**If the service is NOT running:**

Prints a warning message.

Restarts the service using systemctl restart.

**Use Case:** Ensure critical services stay up

## 3. Backup Script

**Use Case:** Automate config backups before updates or deployments.

```
#!/bin/bash

timestamp=$(date +%F)

backup_dir="/backup"

src="/etc"

mkdir -p $backup_dir

tar -czf $backup_dir/etc-backup-$timestamp.tar.gz $src

echo "Backup completed: $backup_dir/etc-backup-$timestamp.tar.gz"
```

**explanation:**

**1** `timestamp=$(date +%F)`

Runs the **date** command and formats it as **YYYY-MM-DD (+%F).**

Stores it in the **variable** timestamp, so each backup has a unique date-based filename.

**ex:**

`echo $timestamp`

**output**: 2025-05-20

**2** **Define the Backup Directory & Source**
`
backup_dir="/backup"

src="/etc"
`

**backup_dir="/backup"** → The folder where backups will be stored.

**src="/etc**" → This is the source directory, where important system configurations reside.

**3** **Ensure the Backup Directory Exists**

`mkdir -p $backup_dir`

Creates the /backup directory if it doesn’t exist.

**-p** → Prevents errors if the folder is already there.

**4** **Compress & Archive the /etc Directory**

`
tar -czf $backup_dir/etc-backup-$timestamp.tar.gz $src
`

`tar` → Command for archiving files.

`-c` → Create a new archive.

`-z` → Use gzip compression to reduce file size.

`-f` → Saves the archive with a specific filename.

`$backup_dir/etc-backup-$timestamp.tar.gz` → The backup file, named with the timestamp.

`$src` → The source directory being backed up (/etc).

**output**: /backup/etc-backup-2025-05-20.tar.gz

**5 . Confirm Backup Completion**

`echo "Backup completed: $backup_dir/etc-backup-$timestamp.tar.gz"
`
Prints a message confirming that the backup was successful.


## 5. User Creation Script

**Use Case:** Onboard users with automated access provisioning.
```
#!/bin/bash

read -p "Enter new username: " username

sudo useradd -m $username

sudo passwd $username

echo "User $username added successfully."
```





