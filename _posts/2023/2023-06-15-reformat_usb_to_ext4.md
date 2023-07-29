---
title: Reformat USB Device to EXT4
date: 2023-06-15 12:00:00 -0500
categories: [linux, storage]
tags: [linux,storage]
---

<img src="/assets/img/posts/2023/reformat_usb_to_ext4/reformat_usb_to_ext4.png" alt="Reformat USB Device to EXT4" style="height:400px; width:600px;" />


If you're using a RHEL machine and need to view USB external devices, you might need to reformat the USB device to the EXT4 file system. In this blog post, we will guide you through the process. Let's get started!

## Reformatting the USB Device

1. Obtain a copy of the latest Linux Rescue disk.
   * You can down the Linux Resuce Disk from [here](https://www.system-rescue.org/Download/).
2. Boot from the Linux Rescue disk.
3. Select the option that states "directly start the graphical environment".
4. Click the GParted tool at the bottom left of the screen.
5. On the top right of the GParted screen, click the dropdown menu and select the external USB device (`/dev/sdb`).
6. Delete all partitions on the external USB device, then click the green checkbox at the top.
7. Click Apply/Close.
8. Right-click on unallocated space, click New, set the Filesystem to `ext4`, and click the green checkbox. Then click Apply.

## Mounting the USB Device on a RHEL Machine

1. Run the following command to remove all `usb-storage` modules from the kernel:
   ```bash
   modprobe -r usb-storage
   ```

2. Run the following command to install all usb-storage modules to the kernel:
   ```bash
   modprobe -i usb-storage
   ```
3. Run the following command to read all messages in the kernel and look for the /dev/sdb1 device:
   ```bash
   dmesg
   ```
4. Run the following command to mount the USB device to the /media directory:
   ```bash
   mount /dev/sdb1 /media
   ```

5. Ensure that the necessary mount point is mounted on the machine via /etc/fstab. Open the /etc/fstab file using a text editor:
   ```bash
   /etc/fstab
   ```
    Add the following line to the file : 
      ```bash
      /dev/sdb1 /media ext4 defaults 0 0
      ```
Congratulations! You have successfully reformatted the USB device to the EXT4 file system and mounted it on your RHEL machine. Now you can access and use the USB external device as needed.