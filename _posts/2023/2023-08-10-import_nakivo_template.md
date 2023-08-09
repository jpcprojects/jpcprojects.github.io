---
title: Importing Nakivo OVA Template on Proxmox Server
date: 2023-08-10 01:00:00 -0500
categories: [Proxmox, Nakivo]
tags: [Proxmox, Nakivo, virtualization]
---

<img src="/assets/img/posts/2023/proxmox_cluster_not_ready/proxmox_cluster_not_ready.jpg" alt="Importing Nakivo OVA Template on Proxmox Server" style="height:400px; width:600px;" />


Proxmox is a powerful virtualization platform that allows you to manage your virtual machines efficiently. If you're looking to import a Nakivo OVA template into your Proxmox server, this guide will walk you through the process step by step.

## Prerequisites

Before you begin, make sure you have the following:

- Access to your Proxmox server via SSH.
- The Nakivo OVA file you wish to import.

## Step-by-Step Guide

1 **SSH into the Proxmox Server**

Open your terminal and SSH into your Proxmox server using the following command:

```bash
ssh username@IPADDRESS
```

2 **Create a Working Directory**

Create a directory to organize your import files:

```bash
mkdir ova_import && cd ova_import
```

3 **Download the Nakivo OVA File**

Navigate to the Nakivo website and download the OVA file. You can do this by:

- Visiting https://www.nakivo.com/resources/download/trial-download/
- Entering the required information in the "Download Free Trial" box
- Selecting "Download Free Trial"
- Clicking the "Download" button under the "VMware Virtual Appliance (Full Solution" section

4 **Copy the .ova File to Proxmox Server**

Use the scp command to copy the downloaded OVA file from your host machine to the Proxmox server's working directory:

```bash
scp NAKIVO_Backup_Replication_VA_v10.9.0_Full_Solution_TRIAL.ova root@IPADDRESS:ova_import
```

5 **Create a New VM from the OVA**

Use the qm importovf command to create a new virtual machine from the extracted OVA:

```bash
qm importovf 122 ./NAKIVO_Backup_Replication_VA_v10.9.0_Full_Solution_TRIAL.ovf vmstorage2 --format qcow2
```

6 **Launch the Virtual Machine**

Launch the VM to ensure connectivity:

Right-click on the VM
Select "Start"

## Conclusion

Importing a Nakivo OVA template into your Proxmox server is a straightforward process. By following these steps, you can have your Nakivo instance up and running on your Proxmox environment efficiently.


### Resourceful Websites for Further Information: ###

[Proxmox Official Documentation:](https://pve.proxmox.com/pve-docs/pve-admin-guide.html) The official Proxmox documentation provides detailed information on various aspects of using and managing Proxmox servers.

[Nakivo Knowledge Base:](https://helpcenter.nakivo.com/) Nakivo's knowledge base offers a wealth of articles and guides related to their software, including deployment and configuration on various platforms.