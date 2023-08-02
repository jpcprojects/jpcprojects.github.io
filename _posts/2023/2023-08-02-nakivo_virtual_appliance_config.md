---
title: Nakivo Virtual Appliance Configuration in vCenter
date: 2023-08-02 01:00:00 -0500
categories: [backup, virtualization]
tags: [nakivo, vcenter, virtual appliance]
---

The Nakivo Virtual Appliance is a powerful tool for data protection and disaster recovery in virtual environments. In this blog post, we'll walk you through the step-by-step process of configuring the Nakivo Virtual Appliance in vCenter.

## Prerequisites

Before starting the configuration, make sure you have downloaded the latest OVA file from Nakivo and saved it to a location accessible by vCenter.

## Deploy Nakivo Virtual Appliance

1. **Download the Nakivo OVA File**: Navigate to [Nakivo's trial download page](https://www.nakivo.com/resources/download/trial-download/), enter random information in the "Download Free Trial" box, and select "Download Free Trial." Under the "VMware Virtual Appliance (Full Solution)" section, click "Download" to get the OVA file. Save the .ova file to a location accessible by vCenter.<br>
2. **Launch vCenter**: Access your vCenter web interface by entering the IP address or hostname in the browser.<br>
3. **Deploy OVF Template**: In vCenter, right-click on the necessary host or cluster, and select "Deploy OVF Template."<br>
4. **Select Local File and Upload OVA**: Choose "Local File" and click "Upload Files" to navigate to the location where vCenter has access to the Nakivo OVA file. Select the file and click "Next."<br>
5. **Configure OVF Template**: Provide a name for the virtual machine (e.g., NAKIVO) and select a location for the virtual machine. Then, select a compute resource (e.g., cluster or host). Review the details and accept the license agreements.<br>
6. **Select Storage and Network**: Choose the appropriate storage device and select "Thin Provision" as the virtual disk format. Select the VM Network for network connectivity.<br>
7. **Complete Deployment**: Review all settings and click "Finish" to deploy the Nakivo Virtual Appliance.<br>

## Configure Nakivo Virtual Appliance Networking

1 **Launch Nakivo Virtual Appliance**: After deploying the Nakivo Virtual Appliance, launch the VM from vSphere. The startup may take a few minutes initially but will eventually prompt you to configure networking information.<br>
2 **Navigate to Network Settings**: Set the hostname to "NAKIVO" and configure the network card (ens192) with the following static networking details:
   - DHCP: Disabled
   - IP Address: [IPADDRESS]
   - Netmask: [NETMASK]
   - Gateway: [GATEWAY]<br>
3 **Change Default nkvuser Password**: Navigate to Security Settings and update the nkvuser password for improved security.<br>

## Create Admin Account

1. **Connect to Nakivo Virtual Appliance**: Access the Nakivo Virtual Appliance web interface at https://[IPADDRESS]:4443.<br>
2. **Create Admin Account**: When you first launch the Virtual Appliance web interface, you will be prompted to create an admin account. Provide the following details:
   - Name: [NAME]
   - Username: [USERNAME]
   - Email: [EMAIL]
   - Password: [PASSWORD]

## Configuring a New Share on the Hydrastor

- If you are using a Hydrastor as storage, follow the instructions [here](https://blog.johnsonpremier.net/hydrastor_cifs_share/) to configure the new share.

## Configuring the New NAKIVO Virtual Appliance

1. **Connect to Nakivo Virtual Appliance**: Access the Nakivo Virtual Appliance web interface at https://[IPADDRESS]:4443.<br>
2. **Connect to vCenter**: Under Settings / Inventory, select the + sign / Virtual / VMware vCenter or ESXi Host.
   - Display Name: vCenter
   - Hostname or IP: [IPADDRESS of vCenter]
   - Username: [USERNAME]
   - Password: ****
   - Web Services Port: 443
   - Finish<br>
3. **Create Backup Jobs**: If you are using vCenter/vSphere VMs, follow the instructions [here](https://blog.johnsonpremier.net/nakivo_backup_jobs/) to create backup jobs.<br>



## Conclusion

Configuring the Nakivo Virtual Appliance in vCenter is a crucial step towards ensuring data protection in your virtualized environment. By following the steps in this blog post, you can take advantage of Nakivo's robust features for backup and disaster recovery.

Don't forget to regularly review your backup strategy and test restore procedures to guarantee the integrity of your backups and preparedness for any potential data loss scenarios.
