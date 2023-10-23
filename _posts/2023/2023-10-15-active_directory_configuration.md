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

![join_domain_gui0](/assets/img/posts/2023/active_directory_configuration/join_domain_gui0.png)
![join_domain_gui1](/assets/img/posts/2023/active_directory_configuration/join_domain_gui1.png)


Add the IP address of the domain controller in the `Preferred DNS` box, click `Save`

![join_domain_gui2](/assets/img/posts/2023/active_directory_configuration/join_domain_gui2.png)


Right click on Windows icon and select `System`, then Click `Domain or workgroup` link next to `Related links` section. You will be prompted for admin rights.

![join_domain_gui3](/assets/img/posts/2023/active_directory_configuration/join_domain_gui3.png)

In the `Computer Name` tab, select the `Change` button

![join_domain_gui4](/assets/img/posts/2023/active_directory_configuration/join_domain_gui4.png)


Check the `Domain` box and enter the domain information. Click `OK`

![join_domain_gui5](/assets/img/posts/2023/active_directory_configuration/join_domain_gui5.png)


Domain admin credentials are required.

![join_domain_gui6](/assets/img/posts/2023/active_directory_configuration/join_domain_gui6.png)

After successful authentication, a welcome message is displayed. Restart the machine.

![join_domain_gui7](/assets/img/posts/2023/active_directory_configuration/join_domain_gui7.png)
![join_domain_gui8](/assets/img/posts/2023/active_directory_configuration/join_domain_gui8.png)
![join_domain_gui9](/assets/img/posts/2023/active_directory_configuration/join_domain_gui9.png)

You may now authentication with any domain user. Click on `Other user` and authentication with a domain user account.

![join_domain_gui10](/assets/img/posts/2023/active_directory_configuration/join_domain_gui10.png)

==========================================================================

## 4. Join Windows Machine to Domain via Powershell

Login as a user who has local admin rights and launch powershell as admin

Display network interfaces
```powershell
Get-NetIPInterface -AddressFamily IPv4
```

![join_domain_powershell0](/assets/img/posts/2023/active_directory_configuration/join_domain_powershell0.png)


Change DNS setting to refer to AD DS domain controller
```powershell
Set-DnsClientServerAddress -InterfaceIndex 7 -ServerAddresses “192.168.1.113” -PassThru
```

![join_domain_powershell1](/assets/img/posts/2023/active_directory_configuration/join_domain_powershell1.png)

Join to the domain. 
- For `username` add the correct domain user
- For `userpassword` add the correct password for that user
```powershell
Add-Computer -DomainName “jpc.net” -Credential (New-Object PSCredential “username”, (ConvertTo-SecureString -AsPlainText “userpassword” -Force))
```

Restart the computer
```powershell
Restart-Computer -Force
```

After restarting, verify to logon as a domain user

![join_domain_powershell2](/assets/img/posts/2023/active_directory_configuration/join_domain_powershell2.png)

Make sure the domain information is registered correctly

![join_domain_powershell3](/assets/img/posts/2023/active_directory_configuration/join_domain_powershell3.png)


==========================================================================


## 5. Add Active Directory Users via GUI

Launch Server Manager

Click `Tools` / `Active Directory users and Computers`

![add_user_gui0](/assets/img/posts/2023/active_directory_configuration/add_user_gui0.png)

Right click on `Users` on the left and select `New` / `User`

![add_user_gui1](/assets/img/posts/2023/active_directory_configuration/add_user_gui1.png)

Input username and logon for the new user. Click `Next`

![add_user_gui2](/assets/img/posts/2023/active_directory_configuration/add_user_gui2.png)

Set the initial password for the new User. Click `Next`

![add_user_gui3](/assets/img/posts/2023/active_directory_configuration/add_user_gui3.png)

Confirm the details, then click `Finish`

![add_user_gui4](/assets/img/posts/2023/active_directory_configuration/add_user_gui4.png)

A new user has now been added to the domain. This user can now log into any machine that is joined to the domain.

## 6. Add Active Directory Users via Powershell

Launch PowerShell as admin

Show the current list of AD users

```powershell
Get-ADUser -Filter * | Format-Table DistingusihedName
```

![add_user_powershell0](/assets/img/posts/2023/active_directory_configuration/add_user_powershell0.png)

Add a new user, this user will be named `JPCuser`

![add_user_powershell1](/assets/img/posts/2023/active_directory_configuration/add_user_powershell1.png)

Verify the account creation

```powershell
Get-ADUser -Identity JPCuser
```

![add_user_powershell2](/assets/img/posts/2023/active_directory_configuration/add_user_powershell2.png)

### Additional PowerShell Commands

Reset an existing users password

```powershell
Set-ADAccountPassword -Identity JPCuser `
-NewPassword (ConvertTo-SecureString -AsPlainText “0qpvP45Y4DZm29t8” -Force) `
-Reset
```

![add_user_powershell3](/assets/img/posts/2023/active_directory_configuration/add_user_powershell3.png)

Delete a user account

```powershell
Remove-ADUser -Identity “CN=JPCuser,CN=Users,DC=JPC,DC=net”
```

**Select the `Yes to All]` option.**

![add_user_powershell4](/assets/img/posts/2023/active_directory_configuration/add_user_powershell4.png)

==========================================================================


## 7. Join CentOS 9 / RHEL 9 Machine to Active Directory Domain


![Join CentOS 9 / RHEL 9 to Active Directory Domain](/assets/img/posts/2023/active_directory_configuration/join_centos_rhel_to_domain.jpg)


Before we begin, it's crucial to ensure that your CentOS 9 or RHEL 9 machine is configured to use the Windows Server 2022 domain controller's IP address as the DNS server. This ensures proper domain resolution and is a prerequisite for joining the machine to the Active Directory domain.

Integrating CentOS 9 or RHEL 9 with a Windows Server 2022 Active Directory domain can streamline user management and enhance security. In this step-by-step guide, we'll walk you through the process of joining a CentOS 9 or RHEL 9 machine to a Windows Server 2022 Active Directory domain. This enables you to use Active Directory credentials for authentication and access control on your Linux system.

**Note:** Before you begin, make sure you have administrative access to both the Linux machine and the Windows Server 2022 domain controller.

**Note:** We are going to use `ABC.NET` as the domain name and `abcdc01.abc.net` as hostname of the domain controller.

## Step 1: Gather Information

First, gather the necessary information:

- **Domain Name:** You'll need the name of your Active Directory domain (e.g., ABC.NET).
- **Administrator Username:** The username of an Active Directory administrator.
- **Administrator Password:** The password for the administrator account.
- **Domain Controller IP or Hostname:** The IP address or hostname of your Windows Server 2022 domain controller.

## Step 2: Install Required Packages

Open a terminal on your CentOS 9 or RHEL 9 machine and enter the following command to install the required packages:

```bash
sudo dnf install -y realmd sssd oddjob oddjob-mkhomedir adcli samba-common-tools krb5-workstation
```

This command installs the necessary tools for integrating with Active Directory.

## Step 3: Join the Domain

Use the `realm join` command to join the Linux machine to the Active Directory domain. Replace the placeholders with your domain information:

```bash
sudo realm join -U ADMIN_USERNAME@DOMAIN_NAME DC_HOSTNAME -v
```

For example:

```bash
sudo realm join -U Administrator@ABC.NET abcdc01.abc.net -v
```

You'll be prompted to enter the administrator password. This step establishes the connection to the Active Directory domain.


## Step 4: Configure krb5.conf

Create a custom krb5.conf file to configure Kerberos authentication. Use the following command to create and edit the file:

```bash
sudo nano /etc/krb5.conf
```

Paste the following configuration into the file, adjusting the realm and server details to match your environment:

```bash
[libdefaults]
    default_realm = ABC.NET
    dns_lookup_realm = true
    dns_lookup_kdc = true

[realms]
    YOUR_DOMAIN = {
        kdc = abcdc01.jpc.net
        admin_server = abcdc01.jpc.net
        default_domain = abcdc01.jpc.net
    }
```

Save and exit the text editor.

## Step 5: Restart the SSSD Service

Restart the System Security Services Daemon (SSSD) service to apply the changes:

```bash
sudo systemctl restart sssd
```

## Step 6: Test Login

You can now test the Active Directory integration by logging in with an AD username. Use the id command:

```bash
id YOUR_DOMAIN\\AD_USERNAME
```

Replace `YOUR_DOMAIN` with your Active Directory domain and `AD_USERNAME` with the username you want to test.

# Conclusion

Congratulations!!! You've successfully integrated your CentOS 9 or RHEL 9 machine with a Windows Server 2022 Active Directory domain. This allows you to use Active Directory credentials for authentication and access control on your Linux system, simplifying user management and enhancing security.

Remember that proper access control and security configurations are essential when integrating Linux systems with Active Directory. Always follow best practices to protect your environment.

- To login via the GUI on Linux machine do the following `ABC\user.name`
- To login via the terminal on Linux machine do the following `su JPC\\user.name`


### Below is a script that will help you join to the domain 


```bash
#
#
#
# - IN SUMMARY - This script does the following ...
#... prompts you for the domain name, e.g., ABC.NET, Domain Admin Username, Domain Admin Password, DC IP address ...
#... installs the required packages ...
#... joins the domain using realm ...
#... creates a custom /etc/krb5.conf file ...
#... restarts the sssd service and gives you the opportunitiy to log into AD with a AD user account for testing ...
#
# *** To login via the GUI on Linux machine do the following [ABC\user.name] ***
# *** To login via the terminal on Linux machine do the following [su ABC\\user.name] ***
#
#!/bin/bash

# Prompt the user for Active Directory domain name, Administrator username, and password
read -p "Enter the Active Directory domain name ex: ABC.NET: " DOMAIN_NAME
read -p "Enter the Administrator username: " ADMIN_USERNAME
read -s -p "Enter the Administrator password: " ADMIN_PASSWORD
echo  # Add a newline after password input

# Prompt the user for the IP address or hostname of the domain controller
read -p "Enter the IP address or hostname of the domain controller: " DC_HOSTNAME

# Install required packages
sudo dnf install -y realmd sssd oddjob oddjob-mkhomedir adcli samba-common-tools krb5-workstation

# Join the Active Directory domain using realm
sudo realm join -U $ADMIN_USERNAME@$DOMAIN_NAME $DC_HOSTNAME -v

# Create a custom krb5.conf file
cat <<EOL | sudo tee /etc/krb5.conf
[libdefaults]
    default_realm = ABC.NET
    dns_lookup_realm = true
    dns_lookup_kdc = true

[realms]
    JPC.NET = {
        kdc = abcdc01.jpc.net
        admin_server = abcdc01.jpc.net
        default_domain = abcdc01.jpc.net
    }
EOL

# Restart sssd service
sudo systemctl restart sssd

# Perform a test login using an AD username
read -p "Enter an AD username for testing: " AD_USERNAME
id $DOMAIN_NAME\\$AD_USERNAME

# Display completion message
echo "Configuration completed. You can now log in with AD credentials."
```

==========================================================================


## 8. Add Active Directory Group Accounts via GUI

Launch `Active Directory Users and Computers`

Right click on `Users` , then click on `New` and select `Group`

![add_group_gui0](/assets/img/posts/2023/active_directory_configuration/add_group_gui0.png)

 
Create a name for the group, then leave the Group scope default as `Global` and the Group type default as `Security`. Then press `OK`

![add_group_gui1](/assets/img/posts/2023/active_directory_configuration/add_group_gui1.png)

Now when you navigate back to domain.name/Users you can see the newly created `testgroup` group.

![add_group_gui2](/assets/img/posts/2023/active_directory_configuration/add_group_gui2.png)

Now, to add a user to the group, you may do the following : 
- Right click on the group and select `Properties`
- Select the [Member tab] and select the `Add` button
- Input the username for this group, click `Check Names` then click `OK`

![add_group_gui3](/assets/img/posts/2023/active_directory_configuration/add_group_gui3.png)


## 9. Add Active Directory Group Accounts via PowerShell

Launch PowerShell as admin

Show the current list of AD groups
```powershell
Get-ADGroup -Filter * | Format-Table DistinguishedName
```

![add_group_powershell0](/assets/img/posts/2023/active_directory_configuration/add_group_powershell0.png)

Add a new group named `testgroup2`
```powershell
New-ADGroup testgroup2 `
-GroupScope Global `
-GroupCategory Security `
-Description “Testing Group 2”
```

Verify the creation of the group
```powershell
Get-ADGroup -Identity testgroup2
```

![add_group_powershell1](/assets/img/posts/2023/active_directory_configuration/add_group_powershell1.png)

Delete a user from a group

```powershell
Remove-ADGroupMember -Identity testgroup2 -Members jamison.johnson
```

Delete a group

```powershell
Remove-ADGroup -Identity testgroup2johnson
```

## 10. Add Active Directory Organizational Units (OUs) via GUI

Launch `Active Directory Users and Computers`

Right click on your domain name on the left tree and select `New` then `Organizational Unit`

![add_ou_gui0](/assets/img/posts/2023/active_directory_configuration/add_ou_gui0.png)

Create a name for your OU, then click `OK`

![add_ou_gui1](/assets/img/posts/2023/active_directory_configuration/add_ou_gui1.png)

A new OU called `Testing` is now created.

![add_ou_gui2](/assets/img/posts/2023/active_directory_configuration/add_ou_gui2.png)


## 11. Add Active Directory Organizational Units (OUs) via PowerShell

Launch PowerShell as Admin

Show the current list of AD groups
```powershell
Get-ADOrganizationalUnit -Filter * | Format-Table DistinguishedName
```

![add_ou_powershell0](/assets/img/posts/2023/active_directory_configuration/add_ou_powershell0.png)

Add the `testing2` organizational unit
```powershell
New-ADOrganizationalUnit Testing2 `
-Path “DC=jpc,DC=net” `
-ProtectedFromAccidentalDeletion $True
```

![add_ou_powershell1](/assets/img/posts/2023/active_directory_configuration/add_ou_powershell1.png)

Verify the creation of the Organizational Unit

![add_ou_powershell2](/assets/img/posts/2023/active_directory_configuration/add_ou_powershell2.png)


.

.

.

.

.




==========================================================================


## Conclusion

In conclusion, the completion of this Active Directory configuration project in December 2022 marked a significant milestone in my system administration journey. Active Directory, as the backbone of many network infrastructures, now stands as a well-structured, secure, and efficiently managed domain environment. The project encompassed essential tasks, from setting up the domain controller to adding user accounts, group accounts, Organizational Units (OUs), and computer accounts. 

By demonstrating both GUI-based and PowerShell-driven approaches, we've expanded our capabilities, enabling me to accommodate a broad spectrum of network management scenarios. This project not only enhanced my expertise in Active Directory administration but also underscored the pivotal role Active Directory plays in modern IT environments. With this robust foundation in place, I am better prepared to tackle future network challenges and evolving requirements, ensuring a secure and organized digital workspace for our organization. Active Directory remains a cornerstone of any network's success, and this project has fortified that foundation.

📝 For more information about Microsoft Active Directory, visit the [Active Directory Domain Services Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview).
