In Linux, **file permissions** control who can **read, write, or execute a file or directory**. They are essential for system **security** and organization.


**Owner** (User): The creator of the file.

**Group**: Users belonging to the assigned group.

**Others**: All other users on the system.


**Each file has three types of access:**

**Read (r or 4)** → View file contents.

**Write (w or 2)** → Modify file contents.

**Execute (x or 1)** → Run files or enter directories.

```
-rwxr-xr--  
 │││ │ │ └─ Others: read only
 │││ │ └── Group: read and execute
 │││ └─── Owner: read, write, execute
 │└──── File type (- = file, d = directory)
 └───── Always starts with file type
```

### **Checking File Permissions**

```
ls -l notes.txt
```

**ex output:**

```
-rw-r--r-- 1 alice developers  4096 May 13 14:00 notes.txt
```

**Breakdown:**

> -rw-r--r-- → permissions

> 1 → number of links

> alice → owner

> developers → group

> 4096 → file size

> May 13 14:00 → modified date

> notes.txt → filename


### Changing Permissions with `chmod`

**Using Symbolic Mode**

Modify permissions using symbols:

Add (+), remove (-), or set (=) permissions.

**Examples:**

```
chmod u+x filename  # Add execute for user
chmod g-w filename  # Remove write for group
chmod o=r filename  # Set read-only for others
chmod u=rwx,g=rx,o= filename  # Set full access for user, read/execute for group, and no access for others
```

### Using Numeric (Octal) Mode

Each permission has a value:

Read (4), Write (2), Execute (1).

**Examples:**

```
chmod 755 filename  # User (rwx), Group (r-x), Others (r-x)
chmod 644 filename  # User (rw-), Group (r--), Others (r--)
chmod 700 filename  # User (rwx), No access for others
```

### **Changing Ownership with `chown`**

```
chown newuser filename  # Change owner
chown newuser:newgroup filename  # Change owner and group
chown :newgroup filename  # Change only group
```

**Recursively change ownership:**

```
chown -R newuser:newgroup directory/
```

**-R → Recursive flag**, meaning it will apply the **change to all files and subdirectories inside directory/.**


### Changing Group Ownership with `chgrp`

```
chgrp newgroup filename  # Change group
chgrp -R newgroup directory/  # Change group recursively
```

### Special Permissions

**Setuid (4) – Run as file owner (mostly used with executables)**

```
chmod 4755 myscript.sh
# 4 → setuid, 755 → normal perms

chmod u+s filename
```

When a user runs this file, it executes as the file's owner.

**Setgid (2) – Files inherit group of the directory**

```
chmod 2755 myfolder
chmod g+s filename  # Set on file
chmod g+s directory/  # Set on directory
```
Files: Users run the file with the group's permissions. Directories: Files created inside inherit the group.


**Sticky Bit (t on others execute bit)**

Used on directories to allow only the owner to delete their files.
```
chmod +t directory/
```
Example: /tmp directory.









