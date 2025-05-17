### Entrypoint of my wsl explanation
I have downloaded wsl in my system and created username & password

**"ubuntu@LAPTOP-L592SHA5:~$:** == in this case , ubuntu is a user , after @ it is a hostname, **":"** this is seperator, "**~**" is a home directory of any user u logged in i.e **(/home/ubuntu)**, "$" is a seperator

The **Linux file structure** is organized in a hierarchical way, **starting from the root directory (/)**.


| Directory                 |              Description                                                     |
|-------------------------  |-------------------------------------------------------------------           |
| **/sbin -> /usr/sbin**  	| System binaries for **administrative** commands (linked to /usr/sbin).  **eg:** commands like usermod,useradd,userdel,chcpu etc     |
| **/bin -> /usr/bin**      |	Essential **user** binaries (linked to /usr/bin).         **eg:** commands like ls, cp, rm                       |
| **/lib -> /usr/lib**	    | Shared libraries and kernel modules (linked to /usr/lib).                    |
 
/lib in this libraries are used by kernel not by users

### **Important System Directories**

| Directory |	Description |
|------------------|------------------------|
|/boot	|Stores files needed for booting the system (not relevant in containers).|
|/usr	|Contains most user-installed applications and libraries.**eg:** /sbin, /bin, /lib|
|/var	|variable data-Stores logs, caches, and temporary files that change frequently **eg:** where we can see logs , caches etc|
|/etc|	Stores system configuration files i.e configuring system .**eg:** like passwd, hosts, network settings|

### User & Application-Specific Directories

|Directory	|Description|
|----------|------------|
|/home	|Default location for **user home directories**.|
|/opt|	Used for installing **optional third-party** software and optional software packages.|
|/srv	|Holds data for **services** like web servers (rarely used in containers).|
|/root|	Home directory for the **root user.**|

### Temporary & Volatile Directories

|Directory|	Description|
|----------|------------|
|/tmp	|Temporary files (cleared on reboot).|
|/run	|Holds runtime data for processes.|
|/proc	|Virtual filesystem for process and system information.|
|/sys|	Virtual filesystem for hardware and kernel information.|
|/dev	|Contains **device files** (e.g., /dev/null, /dev/sda->hard disk).|

### Mount Points   (Used for mounting external storage (USB, hard drives).)

|Directory	|Description|
|----------|------------|
|/mnt|	Temporary mount point for external filesystems.|
|/media	|Mount point for removable media (USB, CDs).|
|/data	|Likely your mounted volume from Windows (C:/ubuntu-data).|
