---
title: Getting Started
date: 2023-05-30 12:00:00 -0500
categories: [homelab, hardware]
tags: [servers,dell,hp,supermicro] #Tag names should always be lowercase
---

<!--This is an HTML comment in markdown. Similar to # in bash -->

<!--Titles can be in H1-H6, whichever format you choose, put that many #'s in front of the title -->

# Welcome

Hello and welcome to my homelab site! \
This will be awesome!!!!!

# Introduction 
Johnson Premier Consulting is here to provide IT consulting and technical support for those in need. From startups to more established organizations, we provide stellar services. Our expert IT Consultants will make your relationship with technology enjoyable.

<!--*'s will help you create unordered lists -->

# Listing My Information


* Item 1
* Item 2
* Item 3
* Item 4
* Item 5
* Item 6
* Item 7

<!-- ``` data inside ``` will help you create code blocks -->

<!-- below is a bash code block -->

## BASH code block...
```bash
yum update all -y
```

<!-- below is a yml code block -->

## YAML code block...

```yml
---
  - hosts: all
    tasks:
      - name: Ping all machines
        action: ping
```

<!-- below is commented out, because it's not working on the github site, but it is working locally. When I comment out the ## Photos section, the website updates correctly. ** NEED TO TROUBLESHOOT ** It appears that the files MUST be .jpg, when I had a .png file the image didn't load.
-->

## Photos

This is an example of an image being added to markup.

![Getting Started](/assets/img/posts/getting-started.jpg)

_Getting Started_

<!-- 

You can also add an image with the below text. It works great for resizing, however, the image does not show up in the preview section of VSCode, it shows up as a broken image, but it works on the website.

-->

<img src="/assets/img/posts/2023/rhel-unlock/rhel-unlock.jpg" alt="RHEL Unlock" style="height:400px; width:600px;" />

<!-- 
-->

<!-- 
*** is a page break; 3 stars or more is a page break in markdown
-->

***

## Color

<span style="color:red"> **This is really red text** </span>


## Links

🔗 Review the Markdown Cheat Sheet at <https://www.markdownguide.org/cheat-sheet/>

🔗 Review the [Official HP Website](https://hp.com)


<br>
<br>