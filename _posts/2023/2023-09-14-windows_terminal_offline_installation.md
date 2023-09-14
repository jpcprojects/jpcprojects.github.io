---
title: Installing Windows Terminal on an Offline Windows 10 Machine
date: 2023-09-14 01:00:00 -0500
categories: [windows, offline]
tags: [windows, offline]
---

![Installing Windows Terminal on an Offline Windows 10 Machine](/assets/img/posts/2023/windows_terminal_offline_installation/windows_terminal_offline_installation.png)


Windows Terminal is a powerful tool for command-line users, providing a modern and efficient way to interact with your computer. However, what if you need to install it on a Windows 10 machine that doesn't have internet access? Don't worry; we've got you covered. In this guide, we'll walk you through the steps to install Windows Terminal offline.

## Prerequisites

Before we begin, you'll need access to a machine with internet connectivity to download the necessary files.

### On a Machine with Internet Access

1 **Download Windows Terminal**:
   * Navigate to [Microsoft Terminal Releases](https://github.com/microsoft/terminal/releases).
   * Download `Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe.msixbundle`.

2 **Rename and Extract**:
   - Rename the downloaded file to `Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe.zip`.
   - Extract this ZIP file to create the `Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe` directory.

3 **Extract Cascadia Package**:
   - Open the `Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe` directory.
   - Extract `CascadiaPackage_1.17.11461.0_x64.msix` to create the `CascadiaPackage_1.17.11461.0_x64` directory.

4 **Remove Conflicting Files**:
   - From the `CascadiaPackage_1.17.11461.0_x64` directory, move the following files to a different location (e.g., your desktop) as they may cause conflicts:
     - AppxMetadata
     - AppxBlockMap.xml
     - AppxSignature.p7x

### On the Offline Machine

1 **Enable Debug Mode**:
   - Right-click on the Start button.
   - Select "Settings."
   - Go to "Update & Security."
   - Click on "For developers."
   - Turn on "Developer mode."

2 **Copy Files**:
   - Copy the entire `Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe` directory to the root of the C drive on your offline machine.

3 **Register Windows Terminal**:
   - Launch PowerShell ISE as an administrator.
   - Run the following commands:
     ```powershell
     # Navigate to the directory where you copied the CascadiaPackage
     cd C:\Microsoft.WindowsTerminal_1.17.11461.0_8wekyb3d8bbwe\CascadiaPackage_1.17.11461.0_x64
     
     # Register Windows Terminal
     Add-AppxPackage .\AppxManifest.xml -Register
     ```

4 **Launch Windows Terminal**:
   - You should now see the Windows Terminal application in your Start menu.
   - Click on it to launch the application.

That's it! You've successfully installed Windows Terminal on your offline Windows 10 machine. Enjoy the benefits of this versatile command-line tool without needing an internet connection.

Now, you can efficiently work with your command-line tasks, even on machines without internet access.

📝 Explore more about Windows Terminal on their [official GitHub repository](https://github.com/microsoft/terminal/releases).
