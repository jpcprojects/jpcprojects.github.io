---
title: Resize vSphere VM Hard Drive
date: 2023-07-13 01:00:00 -0500
categories: [virtualization]
tags: [virtualization]
---

<img src="/assets/img/posts/2023/resize_vsphere_vm_hd/resize_vsphere_vm_hd.jpg" alt="Resize vSphere VM Hard Drive" style="height:400px; width:600px;" />


# Resize vSphere VM Hard Drive

If you're working with a vSphere VM and need to resize the hard drive to allocate more space, this blog post will guide you through the process. We'll walk you through the steps to resize the hard drive on a vSphere VM. Let's get started!

## Prerequisites

Before proceeding with the resizing process, ensure that you have the following:

- Access to vSphere management interface.
- Administrative privileges to perform VM-related operations.

## Resizing Steps

Follow the steps below to resize the vSphere VM hard drive:

1. Create a backup directory for the current home files:
```bash
mkdir /opt/home.backup
```

2. Move the existing home files to the backup directory:
```bash
cd /home
mv * /opt/home.backup
```

3. View the logical volumes on the machine to identify the home logical volume:
```bash
lvdisplay -v
```

4. Unmount the home directory:
```bash
umount home/
```

5. Verify that the home directory is unmounted:
```bash
df -h
```

6. Comment out or delete the /home mountpoint in the /etc/fstab file using a text editor:
```bash
vi /etc/fstab
#/dev/mapper/home /home xfs defaults,nosuid,nodev 0 0
```

7. Remove the logical volume 'home':
```bash
lvremove /dev/mapper/home
```

8. Extend the logical volume 'root' '/':
```bash
lvextend -l 100%FREE /dev/mapper/root
```

9. Extend the XFS filesystem:
```bash
xfs_growfs -d /dev/mapper/root
```

10. Verify that the 'root' '/' partition has reclaimed the space from 'home':
```bash
df -h
```

11. Move the files from the backup directory back to the home directory:
```bash
cd /opt/home.backup
mv * /home
```

12. Reboot the VM for the changes to take effect:
```bash
reboot
```

<br>

You have successfully resized the hard drive on your vSphere VM. The VM now has more space allocated to the root partition ('/'), allowing you to utilize the additional storage!

