### Entrypoint of my wsl explanation
I have downloaded wsl in my system and created username & password

**"ubuntu@LAPTOP-L592SHA5:~$:** == in this case , ubuntu is a user , after @ it is a hostname, **":"** this is seperator, "**~**" is a home directory of any user u logged in i.e **(/home/ubuntu)**, "$" is a seperator

The **Linux folder structure** is organized in a hierarchical way, **starting from the root directory (/)**.


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
|/usr	|Contains most user-installed applications and libraries.|
|/var	|Stores logs, caches, and temporary files that change frequently.|
|/etc|	Stores system configuration files.|
