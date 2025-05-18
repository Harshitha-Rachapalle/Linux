## Network files

| File                                     | Purpose                                             |
| ---------------------------------------- | --------------------------------------------------- |
| `/etc/hosts`                             | Maps hostnames to IP addresses locally.             |
| `/etc/hostname`                          | Sets the machine’s hostname.                        |
| `/etc/resolv.conf`                       | Lists DNS servers used for name resolution.         |
| `/etc/netplan/*.yaml`                    | YAML-based network config in newer Ubuntu versions. |
| `/etc/sysconfig/network-scripts/ifcfg-*` | Red Hat/CentOS interface configs.                   |

## Important Networking Commands

**1. ifconfig (Legacy, from net-tools package)**

`ifconfig` - Used to view and configure network interfaces

To bring up/down an interface:
```
sudo ifconfig eth0 up
sudo ifconfig eth0 down
```

**2. ip (Modern replacement for ifconfig)**

 More powerful and recommended.

 `ip a  ` # checks ip address

 **add or remove ip address**
 ```
sudo ip addr add 192.168.1.50/24 dev eth0
sudo ip addr del 192.168.1.50/24 dev eth0
```

`ip route`   - Great for debugging routing issues 

**3. ping – Test Network Connectivity**

```
ping google.com
```

**4. netstat – Show network connections**

used to see open ports, routes, connections.
```
netstat -tuln    # List listening ports
netstat -plant   # Show processes using network
netstat -tnlp
```

**Breakdown of the Flags**
-**p** → Shows the **process ID**(PID) and name for each connection.

-**l** → Displays only **listening ports** (services waiting for connections).

-**a** → Shows all **active and listening** connections.

-**n** → Uses **numeric addresses** instead of resolving hostnames.

-**t** → Filters for **TCP connections** only.

-**u** → Filters for **UDP connections** only

**5.  traceroute / tracepath**
race packet route to a host — helpful for diagnosing routing issues.
```
traceroute google.com
```

**6.nslookup / dig – DNS Lookup Tools**
Useful for checking DNS resolution in CI/CD pipelines and cloud DNS setups.
```
nslookup google.com
dig google.com
```

