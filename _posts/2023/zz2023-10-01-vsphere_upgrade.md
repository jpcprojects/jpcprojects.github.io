---
title: Upgrading VMware ESXi Hosts to 7.0 - A Comprehensive Guide
date: 2023-10-01 01:00:00 -0500
categories: [vmware, vsphere, virtualization, server]
tags: [vmware, vsphere, virtualization, server]
---

![proxmox_upgrade1](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade1.jpg)


In September 2022, a critical project was undertaken to upgrade four VMware ESXi hosts from version 6.7 to the latest 7.0 release. These hosts played a pivotal role in our virtualization infrastructure, and the upgrade was essential to stay current with new features, security enhancements, and performance improvements. This blog post will take you through the meticulous process of planning and executing the upgrade successfully. This project was completed on an air-gapped network.

## Project Overview

### Servers Involved

Four ESXi hosts required upgrading to VMware ESXi 7.0:

We need to replace the boot drive in Server1-Server3. These servers previously had 2GB USB-DOM boot drives that needed to be updated to  new 200GB SSD’s. Below are the steps that were taken.

The plan for these servers are to [backup the ESXi config], [remove the USB-DOM boot drive], [insert the SSD], [install VMware ESXi, 6.7.0, 14320388 via a CD/DVD], [confirm connectivity], [restore the ESXi config], then [update to VMware ESXi, 7.0.3, 19193900.]

 **vSphere Server 1**
   - Initial Version: VMware ESXi 6.7.0, 14320388
   - Upgrade Completed: 09/09/22

 **vSphere Server 2**
   - Initial Version: VMware ESXi 6.7.0, 14320388
   - Upgrade Completed: 09/16/22

 **vSphere Server 3**
   - Initial Version: VMware ESXi 6.7.0, 14320388
   - Upgrade Completed: 09/23/22

We needed to replace the boot drive in Server4. This server had a 4GB USB-DOM boot drive that need to be updated to a new 200GB SSD. Although this 4GB USB-DOM is sufficient for vSphere 7.x, it will be obsolete and not allowed in vSphere 8.x. 

The plan for this one is to just [backup the ESXi config], [remove the USB-DOM boot drive], [insert the SSD], [install VMware ESXi, 7.0.3, 19193900 via a CD/DVD], then [restore the ESXi config].

 **vSphere Server 4**
   - Initial Version: VMware ESXi 7.0.3, 19193900
   - Upgrade Completed: 09/23/22


![proxmox_upgrade2](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade2.jpg)



## The Upgrade Process

### 1. Backup the ESXi configuration

Before initiating the upgrade process, thorough preparation was essential. This included:

- Creating full backups of all ESXi configurations.

```bash
# SSH into the ESXi host and sync the configuration
vim-cmd hostsvc/firmware/sync_config

# Back up ESXi configuration
vim-cmd hostsvc/firmware/backup_config
```

- As a result, you’ll receive a link to download the configBundle.tgz archive file from the ESXi host. You should replace the asterisk with the IP address of your ESXi host. The archive file that contains the ESXi configuration backup is saved to the /scratch/downloads directory for a short period of time (a few minutes). 
o	Navigate to http://IPADDRESS/downloads/******.tgz via a web browser and download the configBundle.tgz file to your local machines ~Downloads folder.


### 2. Upgrading to VMware ESXi 7.0

#### For LCSVS01, LCSVS02, and LCSVS03 (vSphere Upgrade and Boot Drive Replacement):

- [Download](https://customerconnect.vmware.com/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0) the VMware ESXi 6.7 NEC Custom Image for VMware ESXi 6.7 U3 Install CD.
  - Click on Products and Accounts/My Products
  - Click on All Products tab;  select View Download Components next to VMware vSphere;
  - Select Version 7.0 from the dropdown menu
  - Click on Custom ISOs tab 
  - We are using NEC hosts in the  lab, so we will download the [NEC Custom Image for VMware ESXi 7.0 U3 Install CD] file by clicking on [go to downloads] link.


-	Burn this image to a DVD
-	Remove the server from the rack, remove the old boot drive [USB-DOM 2GB] and install the new boot drive [Intel SSD 200GB]








📝 For more information about Proxmox updates, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
