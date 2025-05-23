## Boot process & troubleshooting

### Step 1: BIOS/UEFI – The First Gatekeeper

✅ When the server powers on, the **BIOS/UEFI firmware performs a hardware check called POST** (Power-On Self-Test).

✅ Checks CPU, RAM, disk, and connected peripherals.

✅ If an issue is found (e.g., corrupted hardware or misconfigured boot order), it may throw boot errors. 

✅ The firmware then hands control to the boot loader (GRUB).

checks BIOS settings and boot order using:

```
sudo dmidecode | less
```

### Step 2: GRUB (Boot Loader) – Selecting the Right Kernel

✅ GRUB (Grand Unified Bootloader) is **responsible for loading the Linux kernel**. 

✅ It presents a boot menu allowing selection of different kernel versions. 

✅ If misconfigured, the system may hang at the GRUB prompt.

* manually edits GRUB to select an older working kernel:
  
  At the GRUB menu: 1️⃣ Press e to edit the boot entry.

   2️⃣ Locate the kernel line.

  3️⃣ Modify kernel parameters or try a previous version.

  4️⃣ Press Ctrl + X to boot.

If GRUB itself fails, reinstalls it manually using:
```
sudo grub-install /dev/sda
```

### Step 3: Kernel Initialization – Loading Core System Components

Once GRUB hands over control, the Linux kernel boots up and initializes:

✅ Hardware drivers (network, storage, peripherals).

✅ Essential modules required for booting the operating system. 

✅ The root filesystem (/), mounting disks.

checks for kernel panic errors using:
```
journalctl -k -b
```
If a kernel panic occurs, she boots into a previous working kernel using:
```
sudo grub-reboot "Previous Kernel"
```

### Step 4: initramfs – Preparing the Root Filesystem

 ✅ initramfs (initial RAM filesystem) loads essential drivers before fully mounting the disk.
 
 ✅ If corrupted, the system might throw a "No root filesystem found" error.

to fix missing drivers we should rebuilds `initramfs` 
```
sudo update-initramfs -u -k $(uname -r)
```
### Step 5: systemd – Bringing Up Services & The System

 ✅ The first user-space process (systemd) starts running.
 
 ✅ Loads all configured services (networking, logging, SSH).
 
 ✅ If a service hangs, the boot process stalls.

💡 we can  checks failing services using:

```
systemctl list-units --failed
```
She disables problematic services to allow boot:

```
sudo systemctl disable failing-service
sudo reboot
```

### Step 6: User Login – System Ready for Use

The boot completes, and users log into the system via SSH or GUI.

✅ If login doesn’t work,i'll checks getty@.service. ✅ If SSH fails, she restarts the SSH service:

```
sudo systemctl restart sshd
```
