---
title: Install Apache NetBeans on RHEL 8 Machine
date: 2023-06-27 01:00:00 -0500
categories: [netbeans, rhel, linux]
tags: [netbeans,rhel,linux]
---

Apache NetBeans is a powerful integrated development environment (IDE) for Java, PHP, and other programming languages. In this blog post, we will walk you through the step-by-step process of installing Apache NetBeans on a RHEL 8 machine. Let's get started!!

## Prerequisites

Before proceeding with the installation, ensure that you have the following:

- A RHEL 8 machine with administrative privileges.
- Internet connectivity to download the required packages.

## Installation Steps

Follow the steps below to install Apache NetBeans:

1. Open a terminal on your RHEL 8 machine.
2. Update the system packages using the following command:
```bash
sudo dnf update -y
```
3. Install the Java Development Kit (JDK) by running the following command:
```bash
sudo dnf install java-11-openjdk-devel -y
```
4. Confirm Java is installed by quering the version.
```bash
java -version
```
5. Change to the /tmp directory
```bash
cd /tmp
```
6. Download NetBeans IDE Version 18 using the wget command
```bash
wget https://archive.apache.org/dist/netbeans/netbeans-installers/18/apache-netbeans-18-0.noarch.rpm
```
7. Run the installer
```bash
sudo rpm -Uvh apache-netbeans-*.noarch.rpm
```
<br>
<br>

**Alternatively**, *you can run the following playbook from an Ansible server to automate this process.*

```yaml
---
- hosts: all
  become: yes
  tasks:
    - name: Install Java
      command: sudo dnf install java-17-openjdk java-17-openjdk-devel -y
    - name: Download NetBeans
      get_url:
        url: https://archive.apache.org/dist/netbeans/netbeans-installers/18/apache-netbeans-18-0.noarch.rpm
        dest: /tmp/apache-netbeans-18-0.noarch.rpm
    - name: Install NetBeans
      command: sudo rpm -Uvh /tmp/apache-netbeans-*.noarch.rpm
```

<br>

You have successfully installed Apache NetBeans on your RHEL 8 machine. The application is listed within your RHEL8 applications menu. You can now start using NetBeans as your preferred IDE for Java, PHP, and other programming languages.

<br>

🔗 For more information and documentation on Apache NetBeans, visit the [Official Apache Netbeans Website](https://netbeans.apache.org)!

