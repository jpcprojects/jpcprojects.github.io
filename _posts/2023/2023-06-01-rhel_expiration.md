---
title: Change RHEL Users Expiration Date
date: 2023-06-01 12:00:00 -0500
categories: [linux, terminal]
tags: [rhel,user_management,terminal]
---

<img src="/assets/img/posts/2023/rhel-expiration/rhel-expiration.jpg" alt="RHEL Unlock" style="height:400px; width:600px;" />


In RHEL (Red Hat Enterprise Linux), you can change a user's expiration date using the terminal. Here's how:

- Open a terminal...
- Switch to the root user or use a user with administrative privileges.
- To view the current expiration date for a user, use the `chage` command with the `-l` option followed by the username:
```bash
chage -l username
```
- To change the expiration date for a user, use the chage command with the -E option followed by the new date in YYYY-MM-DD format:
```bash
chage -E YYYY-MM-DD username
```
  *Replace YYYY-MM-DD with the desired expiration date and username with the actual username.*
    - Note: Make sure to choose an appropriate expiration date based on your requirements and security policies.
- Verify the changes by running the chage -l username command again.
```bash
chage -l username
```

  *Congratulations. That's it!!! You have successfully changed the expiration date for the RHEL user using the terminal.*