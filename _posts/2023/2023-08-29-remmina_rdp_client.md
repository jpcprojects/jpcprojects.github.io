---
title: Remmina RDP Client - Connecting to Windows Machines on RHEL 8
date: 2023-08-29 01:00:00 -0500
categories: [Linux, Remote]
tags: [Linux, Remote]
---

<img src="/assets/img/posts/2023/remmina_rdpclient/remmina_rdpclient.jpg" alt="Remmina RDP Client - Connecting to Windows Machines on RHEL 8" style="height:400px; width:600px;" />

In the realm of remote desktop connections, Remmina stands out as a versatile and powerful tool for accessing Windows machines from your RHEL 8 system. In this blog post, we will walk you through the process of installing the Remmina package on RHEL 8, establishing connections to both Windows 10 and Windows 11 machines, and troubleshooting common connection issues.

## Installing Remmina on RHEL 8

To begin, let's install the Remmina package on your RHEL 8 machine:

1 Open a terminal.<br>
2 Run the following command to install Remmina:<br>
```bash
sudo dnf install remmina -y
```
## Connecting to Windows Machine

Once Remmina is installed, you can effortlessly connect to Windows machines:

1 Launch Remmina from the Application Menu or search.<br>
2 Click the "+" button in the top-left corner to add a new connection.<br>
3 In the "Name" field, provide a recognizable name for the connection.<br>
4 For "Server," input the IP address or hostname of the Windows machine.<br>
5 Choose "RDP - Remote Desktop Protocol" as the protocol.<br>
6 In the "Username" field, enter your Windows user account.<br>
7 Optionally, you can configure other settings like resolution, color depth, and more.<br>
8 Click "Save" to store the connection configuration.<br>

## Troubleshooting Connection Issues

If you encounter the "cannot connect to the RDP server" error, it might be due to Network Level Authentication (NLA) on the Windows machine. Here's how you can disable NLA:

1 On the Windows machine, right-click the "Start" button and select "System."<br>
2 Click "Remote settings" on the left sidebar.<br>
3 Click "Advanced settings"<br>
3 Under the "Configure Network Level Authentication" section, uncheck the "Require computers to use Network Level Authentication (recommended)" option.<br>
4 Click "Apply" and then "OK" to save the changes.<br>

## Conclusion

Remmina simplifies remote desktop connections by providing a user-friendly interface and robust features for connecting to Windows machines from your RHEL 8 system. By following the installation and connection steps outlined above, you can seamlessly access and manage remote Windows systems. In case you encounter connection errors like the "cannot connect to the RDP server" message, remember to disable Network Level Authentication on the Windows machine to resolve the issue.

For more information on RDP and Remmina, consider exploring these valuable resources:

[Remmina Official Documentation:](https://remmina.org/) The official Remmina documentation provides detailed guides, tips, and troubleshooting information for a comprehensive Remmina experience.
