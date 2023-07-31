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
