---
title: Upgrading Ubuntu 18.04 to 20.04 Offline Using Terminal
date: 2023-07-30 01:00:00 -0500
categories: [ubuntu, linux]
tags: [ubuntu,linux]
---

<img src="/assets/img/posts/2023/ubuntu_offline_upgrade/ubuntu_offline_upgrade.jpg" alt="Upgrading Ubuntu 18.04 to 20.04 Offline Using Terminal" style="height:400px; width:600px;" />


Upgrading your Ubuntu system to the latest LTS release can bring new features, improved performance, and security enhancements. If you're dealing with an offline Ubuntu 18.04 machine and want to upgrade to 20.04, fear not! In this blog post, we'll guide you through the process step by step using the command-line tool "do-release-upgrade".

## Preparing for the Upgrade

Before we begin the upgrade process, you need to prepare the Ubuntu 20.04 installation media and transfer it to the offline machine.

- **Prepare Ubuntu 20.04 Installation Media**: Follow the steps mentioned in our previous blog post to download the Ubuntu 20.04 ISO and create a bootable USB/DVD.<br>
- **Transfer the ISO to the Offline Machine**: Copy the downloaded Ubuntu 20.04 ISO file to the offline Ubuntu 18.04 machine using external storage or any other suitable means.<br>


## Backup Your Data (Optional but Recommended)

Before proceeding with the upgrade, it's always a wise idea to create backups of your important data to avoid any potential data loss during the upgrade process.

## Upgrade Process

Now that you have prepared the installation media and backed up your data (if needed), let's move on to the upgrade process.

1. **Mount the Ubuntu 20.04 ISO**: Open a terminal on the Ubuntu 18.04 machine and create a directory where you'll mount the ISO file. For example:
```bash
sudo mkdir /media/ubuntu20.04-iso
```

2. **Mount the ISO to the created directory**
```bash
sudo mount -o loop /path/to/ubuntu-20.04.iso /media/ubuntu20.04-iso
```

3. **Change to the Mounted Directory**: Navigate to the mounted ISO directory:
```bash
cd /media/ubuntu20.04-iso
```

4. **Run the Upgrade**: Initiate the upgrade process using the "do-release-upgrade" command. Use the "-d" flag, indicating that this is a development release (even though 20.04 is an LTS release, the upgrade tool treats it as a development release):
```bash
sudo do-release-upgrade -d
```
*During the upgrade, you may be prompted with various questions. Answer "Y" or "Yes" when asked to continue.*

5. **Follow On-Screen Prompts**: The terminal will display prompts asking you to confirm certain actions. Simply follow the on-screen instructions and respond with "Y" or "Yes" to continue the upgrade process.

6. **Remove the ISO and Reboot**: After the upgrade process completes, you'll be prompted to remove the installation media (ISO file) and reboot the system. To do this, type "y" and press Enter.

7. **Reboot the System**: After removing the ISO and rebooting, your system will now be running Ubuntu 20.04 LTS. Double-check to ensure everything is working correctly and that you have the expected software and configurations in place.

8. **Confirm the Version**: You can confirm the version by running the following command in the terminal:
```bash
less /etc/lsb-release
```

<br>

# Conclusion
You've successfully upgraded your Ubuntu 18.04 machine to Ubuntu 20.04 using the terminal and without internet access. Enjoy the new features and enhancements that come with this Ubuntu LTS release.



