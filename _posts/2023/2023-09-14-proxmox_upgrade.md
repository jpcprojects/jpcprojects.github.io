---
title: Proxmox Server Upgrade
date: 2023-09-14 01:00:00 -0500
categories: [proxmox, server]
tags: [proxmox, server]
---

![proxmox_upgrade1](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade1.jpg)


# Proxmox Server Upgrade: From 7.4-3 to 8.x

In August 2023, I embarked on an exciting project to upgrade four Proxmox servers from version 7.4-3 to the latest Proxmox VE 8.x release. This upgrade was a critical step to ensure that our virtualization infrastructure remained up-to-date with the latest features, security enhancements, and performance improvements. In this blog post, I'll take you through the journey of planning and executing this upgrade successfully.

Released on June 22, 2023, Proxmox VE 8 introduces several notable enhancements over its predecessor, version 7.4-x. These upgrades include upgrading of the [Proxmox Backup Server (PBS) 3.0](https://pbs.proxmox.com/wiki/index.php/Roadmap#Proxmox_Backup_Server_3.0), offering integrated, automated backup solutions. This feature streamlines the backup process, enhancing data protection and recovery capabilities. Furthermore, Proxmox VE 8 elevates container management with the integration of LXC 4.0 and the latest version of Docker, providing improved container orchestration and efficiency. The adoption of the latest [Ceph storage solution](https://pve.proxmox.com/pve-docs/pveceph.1.html#:~:text=Ceph%20is%20a%20distributed%20object,Snapshot%20support) to enhance storage scalability and reliability, making it an optimal choice for handling larger workloads. Enhanced security features, such as improved certificate handling and secure boot support, reinforce the platform's defense against evolving cyber threats. The refreshed web-based management interface ensures a more user-friendly experience, simplifying the management of virtualization infrastructure.

## Project Overview

### Servers Involved

We had four Proxmox servers in our environment, and all of them required an upgrade to Proxmox VE 8.x.

 **Proxmox Server A**
   - Initial Version: Proxmox VE 7.4-3
   - Upgrade Completed: 08/04/23

 **Proxmox Server B**
   - Initial Version: Proxmox VE 7.4-3
   - Upgrade Completed: 08/11/23

 **Proxmox Server C**
   - Initial Version: Proxmox VE 7.4-3
   - Upgrade Completed: 08/18/23

 **Proxmox Server D**
   - Initial Version: Proxmox VE 7.4-3
   - Upgrade Completed: 08/25/23


![proxmox_upgrade2](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade2.jpg)



## The Upgrade Process

### 1. Preparing for the Upgrade

Before initiating the upgrade process, thorough preparation was essential. This included:

- Creating [full backups](https://blog.johnsonpremier.net/proxmox_vm_backup/) of all virtual machines (VMs) and server configurations.
- Verifying [hardware compatibility](https://blog.johnsonpremier.net/proxmox_hardware_compatibility/) with Proxmox VE 8.0.
- Ensuring sufficient disk space and resources for the upgrade process.
- Notifying stakeholders of the planned maintenance window.


### 2. Upgrading Proxmox

The upgrade itself was executed in a phased approach, one server at a time, to minimize disruption. Here are the general steps for each server:

#### Proxmox Server A (08/05/23)

- **Backup**: We backed up all VMs and server configurations again, just before the upgrade, for added safety.
- **Upgrade Process**: 
  - Stop all VMs and containers that are running on the server.
  - SSH into the server.
  - Run the following commands:
    ```
    # disable proxmox commercial repo
    sed -i "s/^deb/\#deb/" /etc/apt/sources.list.d/pve-enterprise.list
    # add the proxmox community repo, if you are not already using it
    echo "deb http://download.proxmox.com/debian/pve $(grep "VERSION=" /etc/os-release | sed -n 's/.*(\(.*\)).*/\1/p') pve-no-subscription" > /etc/apt/sources.list.d/pve-community.list
    # update software repositories for the current 7.x version that is installed
    apt update
    # install software upgrades for the current 7.x version that is installed
    apt dist-upgrade -y
    ```
    **Note**: 
    
    *Confirm that the update/upgrade was successful by doing the following :*
          
    *Log into the proxmox server GUI, click on the node name on the left side, click Summary, next to the PVE Manager Version you should see the latest proxmox version. In my case, the version was `pve-manager/7.4-16`*


  Run additional  commands:

    ```
    # clean apt cache, to reclaim any space being used by the apt package cache
    apt clean
    # run the upgrade checklist utility, resolve any issues reported before continuing. Check and resolve any errors and warnings before moving forward.
    pve7to8 --full
    # update apt repositories from bullseye (7.x) to bookworm (8.x)
    sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list && sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list.d/pve-community.list && sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list.d/pve-enterprise.list
    # update software repositories, to refresh the apt package listings.
    apt update,
    # install software updates from bookwork/proxmox 8.x
    apt dist-upgrade -y
    ```

    **Note**:

    *Monitor the terminal during the upgrade process because you will be prompted to answer questions about services and or configuration files. I typically press `Enter` unless I know I want to make a specific change.*

  Run the final commands:

    ```
    # clean apt cache, to reclaim any space being used by the apt package cache
    apt clean
    # reboot
    reboot now
    ```

- Continue with post-upgrade verification, as explained below.


![proxmox_upgrade3](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade3.jpg)


#### Proxmox Server B (08/10/23)

- **Backup**: Similar to Proxmox Server A.
- **Upgrade Process**: Similar to Proxmox Server A.
- Continue with post-upgrade verification.

#### Proxmox Server C (08/15/23)

- **Backup**: Similar to Proxmox Server A.
- **Upgrade Process**: Similar to Proxmox Server A.
- Continue with post-upgrade verification.

#### Proxmox Server D (08/20/23)

- **Backup**: Similar to Proxmox Server A.
- **Upgrade Process**: Similar to Proxmox Server A.
- Continue with post-upgrade verification.

### 3. Post-Upgrade Verification

Following each server's upgrade, we conducted thorough testing and verification. This included:

- Validating the functionality of all VMs.
- Testing backups and restore processes.
- Monitoring system performance to identify and address any issues promptly.

![proxmox_upgrade4](/assets/img/posts/2023/proxmox_upgrade/proxmox_upgrade4.jpg)


## Conclusion

The journey of upgrading our Proxmox servers from version 7.4-3 to 8.x was a significant milestone in ensuring the reliability and performance of our virtualization infrastructure. By meticulously planning, executing, and testing each upgrade, we minimized downtime and maintained a robust IT environment.

Keeping your virtualization platform up to date is crucial for security, stability, and accessing the latest features. As we move forward, we're excited to leverage the capabilities of Proxmox VE 8.x to meet the evolving needs of our organization.


📝 For more information about Proxmox updates, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).
