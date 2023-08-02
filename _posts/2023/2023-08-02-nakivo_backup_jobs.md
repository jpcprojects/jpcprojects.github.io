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

1. **Log in to Nakivo**: Access the Nakivo Backup & Replication web interface using your credentials. https://IPADDRESS:4443<br>
2. **Add a vSphere Backup Repository**: Before creating a backup job, make sure you have added a vSphere backup repository in Nakivo. This repository is where your VM backups will be stored. To add a repository, navigate to "Settings" > "Inventory" > "Repositories" and follow the on-screen instructions.<br>
3. **Create a Backup Job**: Once you have added the backup repository, navigate to "Jobs" and click on "+ sign" > "VMware vSphere backup job."<br>
4. **Specify Job Name and Description**: Provide a meaningful name and description for your backup job to easily identify its purpose.<br>
5. **Select VMs to Backup**: In the "VMs & Template" section under "View", choose the vSphere virtual machines you want to include in this backup job. You can select individual VMs or entire VM containers like folders, data centers, or clusters.<br>
6. **Choose Backup Repository**: In the "Destination" section, select the previously added vSphere backup repository where Nakivo will store the backups.<br>
7. **Set Backup Schedule**: Configure the backup schedule based on your needs. You can choose to run the backup job once, on a specific date and time, or set up recurring backups with a defined interval.<br>
8. **Enable Advanced Options (Optional)**: Nakivo offers advanced options such as application-aware mode, truncate logs for SQL servers, and pre and post-job scripts. Customize these settings according to your specific requirements.<br>
9. **Enable Global Deduplication (Optional)**: Nakivo offers global deduplication to save storage space by eliminating duplicate data across all backup jobs. You can enable this feature under the "Options" tab.<br>
10. **Review and Finish**: Review all the settings for your backup job. If everything looks good, click "Finish" to create the job.<br>

## Monitoring and Managing Backup Jobs

Once your backup job is created, Nakivo will start backing up your vSphere VMs based on the configured schedule. You can monitor and manage your backup jobs from the "Dashboard" > "Jobs" section of the Nakivo web interface.

## Conclusion

Creating a backup job in Nakivo for backing up your vSphere virtual machines is a straightforward process. With Nakivo Backup & Replication's comprehensive features and user-friendly interface, you can ensure the safety and recoverability of your critical data in your virtualized environment.

Remember to regularly review your backup strategy and test restore procedures to ensure the integrity of your backups and preparedness for any unforeseen data loss scenarios.


