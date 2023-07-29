---
title: How to Fix "Cluster not ready – no quorum? (500)" Error in Proxmox
date: 2023-07-25 12:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox,hypervisor]
---

<img src="/assets/img/posts/2023/proxmox_cluster_not_ready/proxmox_cluster_not_ready.jpg" alt="Cluster not ready - no quorum?" style="height:400px; width:600px;" />


If you encounter the error message "Cluster not ready – no quorum? (500)" in Proxmox, don't worry! In this blog post, we will walk you through the steps to fix this issue and get your Proxmox cluster back up and running smoothly.

## Prerequisites

Before proceeding with the steps to fix the "Cluster not ready – no quorum? (500)" error, make sure you have:

- Access to the Proxmox server with administrative / root privileges.

## Steps to Fix the Error

Follow these steps to resolve the "Cluster not ready – no quorum? (500)" error in Proxmox:

1. **Login to the Proxmox Server**: First, log in to the Proxmox server using your credentials.
2. **Check Cluster State**: Once logged in, check the state of the Proxmox cluster using the following command:
```bash
pvecm status
```
3. **Identify Quorum Activity**: Review the output of the pvecm status command. If you find that the Quorum activity is blocked, it's likely the cause of the error.
4. **Change Votes**: To resolve the issue, execute the following command to change the votes from 2 to 1:
```bash
pvecm expected 1
```
5. **Verify Changes**: After executing the command, re-run **pvecm status** command to verify that the changes have taken effect, and the Quorum activity is no longer blocked.
6. **Resume VM Management**: With the Quorum issue fixed, you should now be able to manage your VMs without encountering the error.

## Conclusion

By following these  steps, you can fix the "Cluster not ready – no quorum? (500)" error in Proxmox and restore the functionality of your Proxmox cluster. Ensuring that the cluster has a healthy Quorum is essential for maintaining high availability and optimal performance!!!