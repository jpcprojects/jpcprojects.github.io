---
title: Creating a CIFS Share on a Hydrastor Storage Device
date: 2023-07-31 01:00:00 -0500
categories: [storage, servers]
tags: [storage,servers]
---

Hydrastor is a powerful storage solution that provides a scalable and reliable platform for storing and managing data. In this tutorial, we will guide you through the process of creating a CIFS share on your Hydrastor storage device using the web-based GUI. Let's get started!

## Prerequisites

Before you begin, make sure you have the following:

- Access to the Hydrastor web-based GUI (https://IPADDRESS:8585)
- Sufficient permissions to create CIFS file structures

## Step-by-Step Guide

1. **Log into Hydrastor GUI**: Open your web browser and navigate to the Hydrastor GUI using the provided IP address and port (e.g., https://IPADDRESS:8585).<br>
2. **Create CIFS File Structure**:
   - Click on "Filesystems" under the Settings section in the left navigation pane.
   - Click the "+ Create" button to start creating a new filesystem.<br>
3. **Filesystem Options**:
   - Set the following options for the new filesystem:
     - Name: DATA
     - Export Target: Hydrastor
     - Export Type: CIFS
     - Filesystem Size: 20 TB
     - Hard Quota: No Hard Quota
     - Soft Quota: No Soft Quota
     - Resilience Level: 3
     - Description: Data Share<br>
4. **Export Options**:
   - For access control, choose "Read/Write" as the Access Mode.
   - Specify the Connectable Clients using IP Address and Subnet Mask (e.g., IP Address/255.255.255.0).<br>
5. **Advanced Options**:
   - Leave all other settings as default.<br>
6. **Create the CIFS Share**:
   - Click the "OK" button to create the CIFS share with the specified configurations.<br>

Congratulations! You have successfully created a CIFS share on your Hydrastor storage device. This share can now be accessed by clients with the specified IP addresses and subnet masks in the Connectable Clients settings.

## Conclusion

Setting up a CIFS share on your Hydrastor storage device enables seamless file sharing and access for your network users. Hydrastor's intuitive web-based GUI makes it easy to manage and configure various storage options, providing a robust storage solution for your organization.














Now that you have prepared the installation media and backed up your data (if needed), let's move on to the upgrade process.

1. **Mount the Ubuntu 20.04 ISO**: Open a terminal on the Ubuntu 18.04 machine and create a directory where you'll mount the ISO file. For example:<br>
```bash
sudo mkdir /media/ubuntu20.04-iso
```
2. **Mount the ISO to the created directory**<br>
```bash
sudo mount -o loop /path/to/ubuntu-20.04.iso /media/ubuntu20.04-iso
```
3. **Change to the Mounted Directory**: Navigate to the mounted ISO directory:<br>
```bash
cd /media/ubuntu20.04-iso
```
4. **Run the Upgrade**: Initiate the upgrade process using the "do-release-upgrade" command. Use the "-d" flag, indicating that this is a development release (even though 20.04 is an LTS release, the upgrade tool treats it as a development release):<br>
```bash
sudo do-release-upgrade -d
```
*During the upgrade, you may be prompted with various questions. Answer "Y" or "Yes" when asked to continue.*<br>
5. **Follow On-Screen Prompts**: The terminal will display prompts asking you to confirm certain actions. Simply follow the on-screen instructions and respond with "Y" or "Yes" to continue the upgrade process.<br>
6. **Remove the ISO and Reboot**: After the upgrade process completes, you'll be prompted to remove the installation media (ISO file) and reboot the system. To do this, type "y" and press Enter.<br>
7. **Reboot the System**: After removing the ISO and rebooting, your system will now be running Ubuntu 20.04 LTS. Double-check to ensure everything is working correctly and that you have the expected software and configurations in place.<br>
8. **Confirm the Version**: You can confirm the version by running the following command in the terminal:
```bash
less /etc/lsb-release
```
<br>

# Conclusion
You've successfully upgraded your Ubuntu 18.04 machine to Ubuntu 20.04 using the terminal and without internet access. Enjoy the new features and enhancements that come with this Ubuntu LTS release.



