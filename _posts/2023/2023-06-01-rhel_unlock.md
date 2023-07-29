---
title: Unlock RHEL Account with Faillock
date: 2023-06-01 12:00:00 -0500
categories: [linux, terminal]
tags: [rhel,user_management,terminal]
---


<img src="/assets/img/posts/2023/rhel-unlock/rhel-unlock.jpg" alt="RHEL Unlock" style="height:400px; width:600px;" />


In RHEL (Red Hat Enterprise Linux), you can unlock a locked user account using the `faillock` command. The `faillock` utility is used to display and modify the login failure records, including unlocking user accounts. Here's how you can do it:


- Open a terminal.

- Switch to the root user or use a user with administrative privileges.

- To view the status of locked user accounts, run the following command:

```bash
faillock --user <username>
```
_Replace <username> with the username of the account you want to unlock._

- If the user account is locked, you will see the account information with the "Account locked" status. To unlock the account, run the following command:

```bash
faillock --user <username> --reset
```
_Replace <username> with the username of the account you want to unlock._

- After executing the command, the account will be unlocked, and you will see a success message indicating that the user account has been reset.

- To verify the account status, you can re-run the faillock --user <username> command. The status should now show as "Account not locked."
That's it!!! You have successfully unlocked a locked RHEL user account using the faillock command. Remember to replace <username> with the actual username of the account you want to unlock...
