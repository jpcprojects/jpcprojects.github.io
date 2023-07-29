---
title: Resolve SSH Keygen Issue
date: 2023-05-31 12:00:00 -0500
categories: [homelab, linux,]
tags: [ssh,linux,] #Tag names should always be lowercase
---

<!--This is an HTML comment in markdown. Similar to # in bash -->

<!--Titles can be in H1-H6, whichever format you choose, put that many #'s in front of the title -->

# Issue : 

- When attempting to ssh into a machine, you receive a similar message.

![SSH Keygen1](/assets/img/posts/2023/ssh_keygen/ssh-keygen1.jpg)

- When you connect to a server via SSH, it gets a fingerprint for the ECDSA key, which it then saves to your home directory under ~/.ssh/known_hosts. This is done after first connecting to the server, and will prompt you with a message like this: 

![SSH Keygen2](/assets/img/posts/2023/ssh_keygen/ssh-keygen2.jpg)


- If you enter 'yes', then the fingerprint is saved to the ~/.ssh/known_hosts file, which SSH then consults every time you connect to that server.
What happens if a server's ECDSA key has changed since you last connected to it? This is alarming because it could actually mean that you're connecting to a different server without knowing it. If this new server is malicious then it would be able to view all data sent to and from your connection, which could be used by whoever set up the server. This scenario is exactly what the "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!" message is trying to warn you about.


# Resolution : 

## Manually Resolve via the known_hosts file :
- In the warning message find the line that tells you where the offending ECDSA key is located in the ~/.ssh/known_hosts file. In this example this line said "Offending ECDSA key in /Users/scott/.ssh/known_hosts:47", which refers to line 47.
Open the ~/.ssh/known_hosts file specified in the warning message
Delete the line specified in the warning message
By deleting this line, your SSH client won't have an ECDSA key fingerprint to compare to, and thus will ask you again to verify the authenticity of the server the next time you connect. Once done, you'll have a new fingerprint in our ~/.ssh/known_hosts file for this server, and the warning will be gone.

## Resolve Using ssh-keygen :
- Run the following command :

```bash
ssh-keygen –R IPADDRESS or HOSTNAME
```


## SSH Key Authentication (Passwordless Authentication)
### Setup SSH Passwordless Authentication
- To enable the passwordless login, we have to put the public key entry of the client machine on the server’s ~/.ssh/authorized_keys (~ = the user’s home directory) file
- Generate a SSH key pair on the management machine and place it on the destinations machine.
```bash
ssh-keygen
```


- You will be asked the following : 
  - Enter file in which to say the key
  - Enter passphrase
  - Enter same passphrase again.
    -  Press Enter all three (3) times.
    
- You can now view the keys that you’ve created on the management machine
```bash
ls –lah ~/.ssh
```

- You will see the id_rsa and id_rsa.pub files
- Copy the id_rsa.pub file to the client machines
```bash
ssh-copy-id –i ~/.ssh/id_rsa.pub username@IPADDRESS
```

- You will be prompted for the password for the remote machine
- Now, in the future, when you ssh into this remote machine from a management machine, you will no longer be prompted for a password.







