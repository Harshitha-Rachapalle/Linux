Linux is a **multi-user operating system**, and its security model is built around **users, groups, and file permissions.**

| File           | Purpose                           |
| -------------- | --------------------------------- |
| `/etc/passwd`  | User account info (username, UID) |
| `/etc/shadow`  | Encrypted passwords               |
| `/etc/group`   | Group info                        |
| `/etc/sudoers` | sudo access configuration         |



### **Creating Users in Linux**

To create a new user in Linux, use:

**useradd Command (For most Linux distributions)**

`useradd username`

This creates a user without a home directory.

To create a user with a home directory:

`useradd -m username`

To specify a shell:

`useradd -s /bin/bash username`

**adduser Command (For Debian-based systems)**

`adduser username`

This is an **interactive command that asks for a password and additional details**.

|Feature|	useradd	|adduser|
|-----|--------------|-------|
|Complexity|	Manual setup|	User-friendly|
|Home Directory|	Requires -m option|	Created automatically|
|Password| Setup	Needs extra commands|	Asked during creation|
|Usage Purpose|	System automation	|Interactive user management|
