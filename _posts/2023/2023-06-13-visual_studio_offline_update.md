---
title: Visual Studio Offline Update
date: 2023-06-13 12:00:00 -0500
categories: [windows, development]
tags: [development,vulnerability,windows]
---

<img src="/assets/img/posts/2023/visual_studio_offline_update/visual_studio_offline_update.jpg" alt="Visual Studio Offline Update" style="height:400px; width:600px;" />


Are you in need of installing Visual Studio 2019 on a machine without internet access? In this blog post, we will guide you through the process of performing an offline installation of Visual Studio 2019. Let's get started!

## Download the Visual Studio Bootstrapper

1. Log into the machine with an account that has access to the internet.
2. Navigate to [https://visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).
3. Under the 2019 option, click "Download".
    - You will be prompted to log into your Microsoft account. A free account will work fine.
4. Save the downloaded file to your local "public downloads" folder.
   - The filename will be similar to "vs_professional__375265950.1556885515.exe".

## Create a Local Install Cache

1. Log into the machine with a local administrator account.
2. To create a complete local layout with all features (this may take a while), follow these steps:
   - Open a command prompt.
   - Execute the following commands:
     ```bash
     cd C:\Users\Public\Downloads
     vs_professional__375265950.1556885515.exe --layout c:\vslayout --lang en-US
     ```
   - **Note: A complete Visual Studio layout requires a minimum of 35-40 GB of disk space.**

## Copy the Local Install Cache to A Network Location or USB Drive

1. Using a NAS or some other type of media that will hold 35-40GB of data, copy the data so it can be transferred to the offline machine.
2. Copy the local install cache to the offline machine to the ~\users\public\public downloads) directory.

## Install Visual Studio from the Local Cache

1. Navigate to the "vslayout" folder and run the "vs_setup.exe" file as an administrator.
2. Click "Continue" when you agree to the Microsoft Software License Terms.
3. Do some research to determine which "Workloads" and/or "Individual components" should be installed.
4. Reboot the system after the installation has completed.

## Register Visual Studio 2019 with a License Key

1. Launch Visual Studio 2019 from the Windows start menu.
2. Click the "Continue without code" link on the bottom right of the screen.
3. Click Help/Register Product.
4. Click the "Unlock with a Product Key" link.
5. Enter the 25-character key obtained from the Microsoft VLSC, and click Apply.
6. Visual Studio 2019 should now be successfully installed and licensed.

Congratulations! You have successfully performed an offline installation of Visual Studio 2019. Now you can start developing your applications with ease.

For more information, you can visit the [Visual Studio Documentation](https://learn.microsoft.com/en-us/visualstudio/windows/)