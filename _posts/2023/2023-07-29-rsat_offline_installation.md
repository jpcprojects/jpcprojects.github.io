---
title: RSAT Configuration on an Offline Windows 11 Machine
date: 2023-07-29 05:00:00 -0500
categories: [windows11]
tags: [windows11]
---

<img src="/assets/img/posts/2023/rsat_offline_installation/rsat_offline_installation.jpg" alt="RSAT Installation & Configuration on an Offline Windows 11 Machine" style="height:400px; width:600px;" />


Remote Server Administration Tools (RSAT) is a set of tools that allows IT administrators to manage Windows Servers remotely from their local machines. In this  post, we will guide you through the process of installing and configuring RSAT on an offline Windows 11 machine. This is useful in scenarios where the target machine does not have direct internet access.

## Prerequisites

Before we begin, ensure you have the following:

- An offline Windows 11 machine where you want to install RSAT.
- A separate online Windows machine with internet access to download the RSAT installer.

## Steps to Complete RSAT Configuration

Follow these steps to install and configure RSAT on an offline Windows 11 machine:

1. **Obtain Access to a Features on Demand disc/data**: More information can be found
[here](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities?view=windows-11).<br>
2. **Copy Data to Local Machine**: Place the disc in the CD/DVD drive or copy the Features on Demand files to the machines C drive. <br>
3. Launch the Services application as admin<br>
4. Start the Windows Update (wuauserv) service<br>
5. Launch PowerShell as a local admin<br>
        Run the following commands:<br>
```bash
cd D: (or to the path in which you saved the Features on Demand files)
```
```bash
Get-WindowsCapability –Online | Where-Object Name –like ‘RSAT*’
```
```bash
Add-WindowsCapability –Online –Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0 –Source .\ -LimitAccess
```
<br>
6. You may repeat these steps to install any RSAT tools or any other tools available within the Features on Demand disc.<br>
        For example, to install **DNS** and **Group Policy**, do the following:<br>
```bash
Add-WindowsCapability –Online –Name Rsat.Dns.Tools~~~~0.0.1.0 –Source .\ -LimitAccess
```
```bash
Add-WindowsCapability –Online –Name Rsat.GroupPolicy.Management.Tools~~~~0.0.1.0 –Source .\ -LimitAccess
```
<br>
7. Reboot and confirm that Active Directory Users and Computers, DNS, and Group Policy Management is installed on your offline Windows 11 machine.<br>

## Conclusion

Congratulations! You have successfully installed and configured RSAT on an offline Windows 11 machine. Now you can remotely manage Windows Servers using RSAT tools, even without direct internet access on the target machine.
