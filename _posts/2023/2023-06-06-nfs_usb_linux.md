---
title: View NTFS USB Device on Linux Machine
date: 2023-06-06 01:00:00 -0500
categories: [linux, storage]
tags: [usb,linux]
---

<img src="/assets/img/posts/2023/nfs-usb-linux/nfs-usb-linux.jpg" alt="View NTFS USB Device on Linux Machine" style="height:400px; width:600px;" />


## Install NTFS-3g from the EPEL Repository

* Ensure that the EPEL repository is configure on the machine

```bash
sudo yum repolist | grep epel
```

* Install NTFS-3G From the EPEL Repository

```bash
yum install ntfs-3g -y
```
## Mounting USB Device on a RHEL Machine

* Unload/Remove the USB storage driver from the Linux kernel

```bash
modprobe -r usb-storage
```

* Install all usb-storage modules to the kernel

```bash
modprobe -i usb-storage
```

* Read all messages in kernel, look for /dev/sdb1 device

```bash
dmesg
```
* Mount the USB drive to the /media directory

```bash
mount /dev/sdb1 /media
```

## Add the USB drive to /etc/fstab so it is persistent upon reboots
* Open the /etc/fstab file

```bash
vi /etc/fstab
```

* Add the following line, then save the file using :wq!
  * /dev/sdb1 /media ext4 defaults 0 0