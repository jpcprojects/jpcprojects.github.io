---
title: Creating a Backup Job in Nakivo for Backing up vSphere Virtual Machines
date: 2023-08-02 01:00:00 -0500
categories: [backup, virtualization]
tags: [nakivo, vsphere, virtual machines]
---

<img src="/assets/img/posts/2023/nakivo_backup_jobs/nakivo_backup_jobs.jpg" alt="Creating a Backup Job in Nakivo for Backing up vSphere Virtual Machines" style="height:400px; width:600px;" />


Data protection is a critical aspect of any virtualization environment. Nakivo Backup & Replication offers a comprehensive solution for backing up vSphere virtual machines, ensuring the safety and recoverability of your data. In this blog post, we'll guide you through creating a backup job in Nakivo to safeguard your vSphere VMs.

## Nakivo Backup & Replication Overview

Nakivo Backup & Replication is a feature-rich backup and disaster recovery software designed specifically for virtual environments. With support for various virtualization platforms, including VMware vSphere, Nakivo offers an easy-to-use interface and powerful backup capabilities.

## Step-by-Step Guide to Create a Backup Job in Nakivo

Follow these steps to create a backup job in Nakivo for your vSphere virtual machines:

1. **Log in to Nakivo**: Access the Nakivo Backup & Replication web interface using your credentials. https://IPADDRESS:4443

2. **Add a vSphere Backup Repository**: Before creating a backup job, make sure you have added a vSphere backup repository in Nakivo. This repository is where your VM backups will be stored. To add a repository, navigate to "Settings" > "Inventory" > "Repositories" and follow the on-screen instructions.

3. **Create a Backup Job**: Once you have added the backup repository, navigate to "Jobs" and click on "+ sign" > "VMware vSphere backup job."

4. **Specify Job Name and Description**: Provide a meaningful name and description for your backup job to easily identify its purpose.

5. **Select VMs to Backup**: In the "VMs & Template" section under "View", choose the vSphere virtual machines you want to include in this backup job. You can select individual VMs or entire VM containers like folders, data centers, or clusters.

6. **Choose Backup Repository**: In the "Destination" section, select the previously added vSphere backup repository where Nakivo will store the backups.

7. **Set Backup Schedule**: Configure the backup schedule based on your needs. You can choose to run the backup job once, on a specific date and time, or set up recurring backups with a defined interval.

8. **Enable Advanced Options (Optional)**: Nakivo offers advanced options such as application-aware mode, truncate logs for SQL servers, and pre and post-job scripts. Customize these settings according to your specific requirements.

9. **Enable Global Deduplication (Optional)**: Nakivo offers global deduplication to save storage space by eliminating duplicate data across all backup jobs. You can enable this feature under the "Options" tab.

10. **Review and Finish**: Review all the settings for your backup job. If everything looks good, click "Finish" to create the job.

## Monitoring and Managing Backup Jobs

Once your backup job is created, Nakivo will start backing up your vSphere VMs based on the configured schedule. You can monitor and manage your backup jobs from the "Dashboard" > "Jobs" section of the Nakivo web interface.

## Conclusion

Creating a backup job in Nakivo for backing up your vSphere virtual machines is a straightforward process. With Nakivo Backup & Replication's comprehensive features and user-friendly interface, you can ensure the safety and recoverability of your critical data in your virtualized environment.

Remember to regularly review your backup strategy and test restore procedures to ensure the integrity of your backups and preparedness for any unforeseen data loss scenarios.




















---
title: Upgrading Ubuntu 18.04 to 20.04 Offline Using Terminal
date: 2023-07-30 01:00:00 -0500
categories: [ubuntu, linux]
tags: [ubuntu,linux]
---

<img src="/assets/img/posts/2023/ubuntu_offline_upgrade/ubuntu_offline_upgrade.jpg" alt="Upgrading Ubuntu 18.04 to 20.04 Offline Using Terminal" style="height:400px; width:600px;" />


Upgrading your Ubuntu system a newer LTS release can bring new features, improved performance, and security enhancements. If you're dealing with an offline Ubuntu 18.04 machine and want to upgrade to 20.04, fear not! In this blog post, we'll guide you through the process step by step using the command-line tool "do-release-upgrade".

## Preparing for the Upgrade

Before we begin the upgrade process, you need to prepare the Ubuntu 20.04 installation media and transfer it to the offline machine.

- **Prepare Ubuntu 20.04 Installation Media**: Download Ubuntu 20.04, or your preferred version of Ubuntu from [here](https://releases.ubuntu.com/focal/) and create a bootable USB/DVD.<br>
- **Transfer the ISO to the Offline Machine**: Copy the downloaded Ubuntu 20.04 ISO file to the offline Ubuntu 18.04 machine using external storage or any other suitable means.<br>


## Backup Your Data (Optional but Recommended)

Before proceeding with the upgrade, it's always a wise idea to create backups of your important data to avoid any potential data loss during the upgrade process.

## Upgrade Process

Now that you have prepared the installation media and backed up your data (if needed), let's move on to the upgrade process.

1 **Mount the Ubuntu 20.04 ISO**: Open a terminal on the Ubuntu 18.04 machine and create a directory where you'll mount the ISO file. For example:<br>
```bash
sudo mkdir /media/ubuntu20.04-iso
```

2 **Mount the ISO to the created directory**<br>
```bash
sudo mount -o loop /path/to/ubuntu-20.04.iso /media/ubuntu20.04-iso
```

3 **Change to the Mounted Directory**: Navigate to the mounted ISO directory:<br>
```bash
cd /media/ubuntu20.04-iso
```

4 **Run the Upgrade**: Initiate the upgrade process using the "do-release-upgrade" command. Use the "-d" flag, indicating that this is a development release (even though 20.04 is an LTS release, the upgrade tool treats it as a development release):<br>
```bash
sudo do-release-upgrade -d
 ```

*During the upgrade, you may be prompted with various questions. Answer "Y" or "Yes" when asked to continue.*<br>

5 **Follow On-Screen Prompts**: The terminal will display prompts asking you to confirm certain actions. Simply follow the on-screen instructions and respond with "Y" or "Yes" to continue the upgrade process.<br>

6 **Remove the ISO and Reboot**: After the upgrade process completes, you'll be prompted to remove the installation media (ISO file) and reboot the system. To do this, type "y" and press Enter.<br>

7 **Reboot the System**: After removing the ISO and rebooting, your system will now be running Ubuntu 20.04 LTS. Double-check to ensure everything is working correctly and that you have the expected software and configurations in place.<br>

8 **Confirm the Version**: You can confirm the version by running the following command in the terminal:
```bash
less /etc/lsb-release
```
<br>

# Conclusion
You've successfully upgraded your Ubuntu 18.04 machine to Ubuntu 20.04 using the terminal and without internet access. Enjoy the new features and enhancements that come with this Ubuntu LTS release.



