---
title: Remove Proxmox Node From Cluster
date: 2023-06-19 01:00:00 -0500
categories: [proxmox, hypervisor]
tags: [proxmox,hypervisor]
---

<img src="/assets/img/posts/2023/remove_proxmox_node_from_cluster/remove_proxmox_node_from_cluster.jpg" alt="Remove Proxmox Node From Cluster" style="height:400px; width:600px;" />


If you need to remove a node from a Proxmox cluster, this blog post will guide you through the process. Whether you are decommissioning a node or migrating to a new one, the steps below will help you successfully remove the node. Let's get started!

## Prerequisites

Before proceeding, ensure that you have the following prerequisites in place:

- Access to a working/running node in the Proxmox cluster.
- Administrative privileges on the Proxmox cluster.

## Removing a Node

Follow these steps to remove a node from the cluster:

1. Delete or migrate any VMs that are running on the node that you want to remove. This step ensures that no active VMs are impacted during the removal process.
2. SSH into a working/running node in the Proxmox cluster.
   ```bash
   ssh username@IPAddress/Hostname
   ```
3. Check which nodes are online in the Proxmox cluster. Run the following command:
   ```bash
   pvecm nodes
   ```
4. Identify the name of the offline node that you want to remove.
5. Delete the offline node using the following command:
   ```bash
   pvecm delnodes <nodename>
   ```
6. After executing the above command, refresh the Proxmox GUI to ensure that the node is fully removed from the cluster.

You have successfully removed a node from your Proxmox cluster! Remember to update your documentation and adjust your cluster configuration as needed.