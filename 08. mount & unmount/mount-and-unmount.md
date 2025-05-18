### What is Mounting?

Mounting is the process of attaching a storage device (partition, USB, DVD, network share) to a directory so that its contents become accessible.

Unmounting removes this link.

**Viewing Devices and Partitions**

`lsblk` - lists blockdevices

`sudo fdisk -l` - provides information about partitions in detail

### Mounting a Filesystem

Assume /dev/sdb1 is a USB device.

### **Step 1:** Create mount point

```
sudo mkdir /mnt/usb
```

**if partition is not available, create a partition**

```
sudo fdisk /dev/sdb
```

Then enter the following in fdisk prompt:

```
n      → create new partition  
p      → primary  
1      → partition number  
[enter] → accept default first sector  
[enter] → accept default last sector  
w      → write changes and exit
```

Now list partitions: using `lsblk`

now we can see /dev/sdb1

### **step 2:** Format the Partition

Format /dev/sdb1 with a file system (e.g., ext4 or vfat):

```
sudo mkfs.ext4 /dev/sdb1
```

### step 3: Mount the Partition

```
sudo mount /dev/sdb1 /mnt/usb
```
### Unmounting

Unmount when you're done or before unplugging:

```
sudo umount /mnt/usb
```

##  Mounting ISO Files (Loop Device)

```
sudo mount -o loop file.iso /mnt/iso
```

**Auto-Mounting on Boot: `/etc/fstab`**
```
sudo nano /etc/fstab
```

## file system types

| Scenario                            | Recommended FS |
| ----------------------------------- | -------------- |
| General-purpose server              | `ext4`         |
| Large log/data storage              | `xfs`          |
| USB/external sharing                | `vfat`, `ntfs` |
| High-resilience data with snapshots | `btrfs`        |
| In-memory cache/temp                | `tmpfs`        |

## Checking Disk Usage

**df – Disk Free**

Shows how much space is used and available on **mounted file systems**.

```
df -h
```
h is human readable

**du – Disk Usage (Per Directory/File)**

```
du -sh
```



