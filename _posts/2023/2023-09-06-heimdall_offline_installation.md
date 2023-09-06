---
title: Install and Configure Heimdall on a RHEL8 Machine Without Internet Access
date: 2023-09-06 01:00:00 -0500
categories: [Docker, Linux]
tags: [Docker, Linux]
---

![Install and Configure Heimdall on a RHEL8 Machine Without Internet Access](/assets/img/posts/2023/heimdall_offline_installation/heimdall_offline_installation.png)


In some environments, you might need to set up Heimdall, a useful dashboard for managing your applications, on a RHEL8 (Red Hat Enterprise Linux 8) machine that lacks internet connectivity. This guide will walk you through the steps to achieve this manually.

## Prerequisites

Before we begin, make sure you have access to a machine with internet connectivity to download and transfer the necessary Docker image files.

## Step 1: Find and Pull the Heimdall Docker Image

Navigate to [Docker Hub](https://hub.docker.com) using an internet-connected machine.

In the search bar, look for the Heimdall Docker image. For example, you can search for "heimdall."

Copy the "docker pull" command provided on the Docker Hub page.  

Execute the "docker pull" command on your internet-connected machine to download the Heimdall Docker image:

```bash
sudo docker pull linuxserver/heimdall
```

Confirm that the Heimdall Docker image has been successfully downloaded:

```bash
sudo docker images
```

## Step 2: Save the Docker Image to a File

To transfer the Docker image to your offline RHEL8 machine, you'll need to save it to a file. Use the following command, replacing "heimdall_image.docker" with your preferred filename:

```bash
sudo docker save -o heimdall_image.docker linuxserver/heimdall
```

*The Docker image file will be saved in the current directory where you ran the command.*

## Step 3: Copy the Docker Image to the Offline Machine

Copy the saved Docker image file (heimdall_image.docker) to your offline RHEL8 machine. You can place it in a temporary directory like "/opt" for easy access.

## Step 4: Load the Docker Image on the Offline Machine

On your offline RHEL8 machine, load the Docker image from the saved file using the following command:

```bash
sudo docker load -i heimdall_image.docker
```

*The Heimdall Docker image will be loaded onto your offline machine.*

## Step 5: Run Heimdall

Copy and paste the following command into the offline machine's terminal to run Heimdall. This command also configures Heimdall to start automatically:

```bash
docker run -d --name=heimdall \
-p 8056:80 \
-p 7543:443 \
-e PUID=1000 \
-e PGID=1000 \
-e TZ=America/New_York \
-v /var/lib/docker/containers/heimdall:/config \
--restart always \
linuxserver/heimdall
```

*After the configuration is complete, reboot the machine for the changes to take effect.*

## Step 6: Verify Heimdall Installation

```bash
sudo docker ps
```

- Access the Heimdall WebGUI using one of the following URLs: <br>
http://IPADDRESS:8056 <br>
http://HOSTNAME:8056 <br>
https://IPADDRESS:7543 <br>
https://HOSTNAME:7543 <br>

## Conclusion

Congratulations! You've successfully installed and configured Heimdall on your RHEL8 machine without internet access. Heimdall provides a centralized dashboard for managing your applications and services.

Now you can efficiently manage your applications, even in environments with limited internet connectivity.

Note: Make sure to check the official website for any updates or additional resources related to Heimdall.


📝 [Heimdall Official Website:](https://heimdall.site/) The official Heimdall website provides awesome information.