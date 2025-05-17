Linux is a **multi-user operating system**, and its security model is built around **users, groups, and file permissions.**

| File           | Purpose                           |
| -------------- | --------------------------------- |
| `/etc/passwd`  | User account info (username, UID) |
| `/etc/shadow`  | Encrypted passwords               |
| `/etc/group`   | Group info                        |
| `/etc/sudoers` | sudo access configuration         |


## for **passwordlessauthentication**, i.e if everytime when we type any command it asks password we can set this by using below command

```
sudo visudo
```
```
ubuntu ALL=(ALL) NOPASSWD: ALL  
```

here ubuntu is a username

If using Nano editor inside visudo, press **Ctrl + X, then Y, then Enter**.


## users

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


**Managing User Passwords**

To set or change a user’s password:

```
passwd username
```
## If we forget a password , we cannot restore it . Instead we can only see encrpted password in /etc/shadow

**Password expiration**: Set password expiry days
```
chage -M 90 username
```

**Lock a user account**
```
passwd -l username
```
**Unlock a user account**
```
passwd -u username
```


|Command	|Description|
|---------|----------|
|sudo chage -M 60 username|	Password expires in 60 days|
|sudo chage -W 7 username|	Warn the user 7 days before expiration|
|sudo chage -I 30 username|	Disable account after 30 days of inactivity|
|sudo chage -E 2025-12-31 username|	Set an exact expiration date|


## **Deleting Users**

To remove a user but keep their home directory:

```
userdel username
```

To remove a user and their home directory:

```
userdel -r username
```

### Groups
Groups are used to manage **permissions for multiple users at once**.

**Creating Groups**
```
groupadd groupname
```

**Adding Users to Groups**
````
usermod -aG groupname username
```

**Viewing Group Memberships**
```
groups username
```


Sudo Access and Privilege Escalation

**Adding a User to Sudo Group**

  On Debian-based systems
```
usermod -aG sudo username
```

On RHEL-based systems:

```
usermod -aG wheel username
```


## Delete a user

 groupdel groupname




