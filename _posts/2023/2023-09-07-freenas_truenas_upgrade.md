---
title: FreeNAS Update to TrueNAS
date: 2023-09-07 01:00:00 -0500
categories: [truenas, freenas, nas, backup]
tags: [truenas, freenas, nas, backup]
---

![freenas_truenas_upgrade1](/assets/img/posts/2023/freenas_truenas_upgrade/freenas_truenas_upgrade1.jpg)


The evolution of data storage and management in the IT world has been nothing short of remarkable. Over the years, FreeNAS and its successor, TrueNAS, have played pivotal roles in this transformative journey. FreeNAS, initially introduced as an open-source network-attached storage (NAS) solution, paved the way for TrueNAS, which brought a new level of enterprise-grade capabilities to the table. In this blog post, we'll delve into the rich history of these two systems, understand why keeping software up to date is crucial, and explore the key differentiators between FreeNAS and TrueNAS. Finally, I'll walk you through the actual update process.

# The Importance of Keeping Software Updated:

Staying up to date with software versions is a fundamental practice in the world of IT for several compelling reasons. First and foremost, software updates often come bundled with critical security patches, shielding your systems from the ever-evolving landscape of cyber threats. Moreover, updates introduce performance enhancements and new features that can boost productivity and efficiency. By embracing the latest versions, you ensure compatibility with evolving hardware and software ecosystems. It's a proactive approach that not only safeguards your data but also keeps your IT infrastructure agile and competitive.

![freenas_truenas_upgrade3](/assets/img/posts/2023/freenas_truenas_upgrade/freenas_truenas_upgrade3.jpg)


# Distinguishing FreeNAS from TrueNAS:

While FreeNAS and TrueNAS share a common lineage, they cater to different ends of the storage spectrum. FreeNAS, rooted in the open-source ethos, offers robust file sharing and storage capabilities suitable for home users and small businesses. On the other hand, TrueNAS extends those capabilities with enterprise-grade features like data deduplication, compression, and high availability, making it an ideal choice for organizations with more substantial storage demands. TrueNAS's commercial counterpart, TrueNAS Enterprise, delivers even greater scalability, data protection, and support options. While FreeNAS is an excellent choice for personal and small-scale use, TrueNAS shines in complex, high-demand environments where reliability and performance are paramount. In this blog post, we'll explore the considerations and steps involved in transitioning from FreeNAS to TrueNAS, helping you make an informed decision for your storage needs.

![freenas_truenas_upgrade3](/assets/img/posts/2023/freenas_truenas_upgrade/freenas_truenas_upgrade2.jpg)


# FreeNAS Update to TrueNAS

In January 2023, I undertook the task of updating two FreeNAS servers to TrueNAS 13.0 U3. This transition involved several planned steps and meticulous execution to ensure a smooth upgrade process. In this blog post, I'll walk you through the entire process, providing detailed instructions and insights.

## Project Overview

### Servers Involved

#### 1. **NAS2 (Backup):**
   - Initial Version: FreeNAS-11.3U3.2
   - Updates:
     - FreeNAS-11.3U3.2 to FreeNAS-11.3U5 (Completed on 11/18/23)
     - FreeNAS-11.3U5 to TrueNAS-12.0U8.1 (Completed on 01/06/23)
     - TrueNAS-12.0U8.1 to TrueNAS-13.0 U3 (Completed on 01/13/23)

#### 2. **NAS1 (Primary):**
   - Initial Version: FreeNAS-11.3U3.2
   - Updates:
     - FreeNAS-11.3U3.2 to FreeNAS-11.3U5 (Completed on 11/18/23)
     - FreeNAS-11.3U5 to TrueNAS-12.0U8.1 (Completed on 01/20/23)
     - TrueNAS-12.0U8.1 to TrueNAS-13.0 U3 (Completed on 01/27/23)

## The Update Process

### 1. Backup FreeNAS Configuration

Before initiating any updates, it's crucial to back up the FreeNAS configuration to ensure data safety and system recovery. Follow these steps:

- Log into FreeNAS.
- Navigate to **System/General/Save Config**.
- Check both checkboxes:
  - Export Password Secret Seed
  - Export Pool Encryption Keys
- Click **Save**.
- Copy the configuration file to a secure location, such as `/network/share/location/FreeNAS_Backups`.

### 2. Apply Update

With the configuration safely backed up, you can proceed with the update process. Follow these steps:

- Log into FreeNAS.
- Navigate to **System/Update**.
- Set the **Update File Temporary Storage Location** to a network share.
- Upload the required `manual-update.tar` file as necessary (located at `/network/share/location/TrueNAS`).
- Click **Apply Update**.

## Conclusion

Updating FreeNAS servers to TrueNAS can be a complex yet necessary task to benefit from the latest features and improvements. With a well-defined plan and careful execution, as outlined in this blog post, you can ensure a successful transition while safeguarding your data and system integrity.

Once everything went well on backup server (NAS2), I repeated the same process for the primary server (NAS1). 

Regularly backing up configurations, updating sofware, and following best practices are key to maintaining a reliable environment.

📝 Investigate more about TrueNAS on their [official documentation hub](https://www.truenas.com/docs/).
