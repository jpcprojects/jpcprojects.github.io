---
title: Active Directory Configuration
date: 2023-10-15 01:00:00 -0500
categories: [active_directory, domain_controller, server]
tags: [active_directory, domain_controller, server]
---

![install_ad_ds0](/assets/img/posts/2023/active_directory_configuration/install_ad_ds0.png)


In December 2022, I embarked on a project to set up and manage an Active Directory environment, a vital component in modern network administration. This venture encompassed a series of tasks aimed at configuring, securing, and managing our Active Directory Domain Services (AD DS). Below, I'll provide a concise summary of each of the key tasks I successfully accomplished during this project.

# Project Overview

## Active Directory Configuration Summary

### 1. Install Active Directory Domain Services (AD DS)
Installed the core foundation, AD DS, which forms the backbone of the entire Active Directory structure.

### 2. Configure the New Domain Controller
Set up the new domain controller, including defining policies, security settings, and administrative parameters to establish a robust network infrastructure.

### 3. Join Windows Machine to Domain via GUI
Demonstrated the process of integrating Windows machines into the Active Directory domain through the graphical user interface, making it accessible to a wide range of administrators.

### 4. Join Windows Machine to Domain via PowerShell
Showcased how to join Windows machines to the domain using PowerShell scripts for a more automated and efficient approach, suitable for bulk deployments.

### 5. Add Active Directory Users via GUI
Explained the process of adding user accounts to Active Directory using the GUI, offering a straightforward method for user management.

### 6. Add Active Directory Users via PowerShell
Introduced the use of PowerShell scripts to create and manage user accounts in bulk, streamlining the user provisioning process.

### 7. Join Linux Machine to Domain via network_configs.sh & adjoin.sh Scripts
Extended Active Directory's reach to Linux machines by detailing how to join them to the domain using network_configs.sh and adjoin.sh scripts.

### 8. Add Active Directory Group Accounts via GUI
Illustrated the creation of group accounts using the GUI, a crucial aspect of Active Directory administration for effective permissions and access control.

### 9. Add Active Directory Group Accounts via PowerShell
Enabled a programmatic approach to group account creation by showcasing the use of PowerShell scripts, ensuring consistent and accurate group management.

### 10. Add Active Directory Organizational Units (OUs) via GUI
Delved into the creation of Organizational Units (OUs) using the GUI, instrumental in organizing objects within the Active Directory domain.

### 11. Add Active Directory Organizational Units (OUs) via PowerShell
Streamlined the process of creating OUs by demonstrating the use of PowerShell scripts, promoting a structured hierarchy within Active Directory.

### 12. Add Active Directory Computer Accounts via GUI
Explained how to add computer accounts using the GUI, simplifying the integration of computers into the domain.

### 13. Add Active Directory Computer Accounts via PowerShell
Provided guidance on using PowerShell scripts to systematically add computer accounts, enhancing efficiency in managing computer resources.

This Active Directory configuration project not only expanded my knowledge but also contributed to building a robust network infrastructure. The tasks undertaken are fundamental in Active Directory management and organization, facilitating user provisioning, permissions control, and network resource management.

   ==========================================================================

## 1. Install Active Directory Domain Services (AD DS)

Launch Server Manager
Click `Manage` / `Add Roles and Features`

![install_ad_ds1](/assets/img/posts/2023/active_directory_configuration/install_ad_ds1.png)

Click `Next`

![install_ad_ds2](/assets/img/posts/2023/active_directory_configuration/install_ad_ds2.png)

Select `Role-based or feature based installation` then click `Install`

![install_ad_ds3](/assets/img/posts/2023/active_directory_configuration/install_ad_ds3.png)

Select the host in which you would like to add AD DS / Click `Next`

![install_ad_ds4](/assets/img/posts/2023/active_directory_configuration/install_ad_ds4.png)

Check the box `Active Directory Domain Services`

![install_ad_ds5](/assets/img/posts/2023/active_directory_configuration/install_ad_ds5.png)

Additional features are requested to install AD DS. Click `Add Features`

![install_ad_ds6](/assets/img/posts/2023/active_directory_configuration/install_ad_ds6.png)

Click `Next`

![install_ad_ds7](/assets/img/posts/2023/active_directory_configuration/install_ad_ds7.png)

Click `Next`

![install_ad_ds8](/assets/img/posts/2023/active_directory_configuration/install_ad_ds8.png)

Click `Install`

![install_ad_ds9](/assets/img/posts/2023/active_directory_configuration/install_ad_ds9.png)

After the installation is finished click `close`

![install_ad_ds10](/assets/img/posts/2023/active_directory_configuration/install_ad_ds10.png)

You have now successfully configured Active Directory Domain Servers (AD DS) on Windows Server 2022.

==========================================================================


## 2. Configure the New Domain Controller

Launch Server Manager

Click `AD DS` / Click the flag icon on the top and select `Promote this server to a domain controller` link

![configure_dc0](/assets/img/posts/2023/active_directory_configuration/configure_dc0.png)

Check the box `Add a new forest` and input your desired domain name information in the `Root domain name` box. Click `Next`

![configure_dc1](/assets/img/posts/2023/active_directory_configuration/configure_dc1.png)


Select `Forest functional level` and `Domain functional level`, the latest available version currently is `Windows Server 2016`, select this option. Set a safe/secure password for Directory Services Restore Mode (DSRM). Click `Next`

![configure_dc2](/assets/img/posts/2023/active_directory_configuration/configure_dc2.png)


In the `DNS Options` section, leave all defaults, click `Next`

![configure_dc3](/assets/img/posts/2023/active_directory_configuration/configure_dc3.png)


Ensure a `NetBIOS domain name`, then click `Next`

![configure_dc4](/assets/img/posts/2023/active_directory_configuration/configure_dc4.png)


Leave the `Paths` section as default, click `Next`

![configure_dc5](/assets/img/posts/2023/active_directory_configuration/configure_dc5.png)


Review your configured settings and click `Next`

![configure_dc6](/assets/img/posts/2023/active_directory_configuration/configure_dc6.png)


Click `Install`, after the install finishes, the system will reboot automatically.

![configure_dc7](/assets/img/posts/2023/active_directory_configuration/configure_dc7.png)


After reboot, the logon named will be changed to `Domain name\` `User name`

![configure_dc8](/assets/img/posts/2023/active_directory_configuration/configure_dc8.png)


==========================================================================


## 3. Join Windows Machine to Domain via GUI

Log into the machine as a local administrator

Change DNS Settings to point to the Domain Controller

- Right click on `Settings`
- Click `Network Connections`
- Click `Ethernet`











==========================================================================


## Conclusion

In conclusion, the completion of this Active Directory configuration project in December 2022 marked a significant milestone in my system administration journey. Active Directory, as the backbone of many network infrastructures, now stands as a well-structured, secure, and efficiently managed domain environment. The project encompassed essential tasks, from setting up the domain controller to adding user accounts, group accounts, Organizational Units (OUs), and computer accounts. 

By demonstrating both GUI-based and PowerShell-driven approaches, we've expanded our capabilities, enabling me to accommodate a broad spectrum of network management scenarios. This project not only enhanced my expertise in Active Directory administration but also underscored the pivotal role Active Directory plays in modern IT environments. With this robust foundation in place, I am better prepared to tackle future network challenges and evolving requirements, ensuring a secure and organized digital workspace for our organization. Active Directory remains a cornerstone of any network's success, and this project has fortified that foundation.

📝 For more information about Microsoft Active Directory, visit the [Active Directory Domain Services Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview).
