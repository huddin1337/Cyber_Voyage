# Kali Linux VM
Today's objective we will be looking at my Kali Linux virtual machine and hardening the virtual machine settings to protect ourselves when conducting various security exercises on this virtual machine. How to establish a secure baseline in which I can use to fall back on when they create other VMS.
1.	We will be changing the default password that i originally configured when installing the linux VM 
 <img width="975" height="231" alt="image" src="https://github.com/user-attachments/assets/44def9d5-596b-45ec-9a49-b1ca43d22a07" />

2.	Unprivileged accounts are used on Linux computers to enhance security and prevent accidental system damage by restricting users from making system-wide chang
<img width="402" height="156" alt="image" src="https://github.com/user-attachments/assets/1b7d003e-b9cf-4003-a7f7-4fcd229060bf" />
<img width="505" height="134" alt="image" src="https://github.com/user-attachments/assets/0e8604d5-9e93-4853-bdfb-6c077bec6d57" />


3.	Each time this baseline is used, it must be updated to ensure that all applications are patched to the most current and secure version
<img width="975" height="177" alt="image" src="https://github.com/user-attachments/assets/ca11133c-7bf4-4ac2-b153-39b1bd8d4960" />
<img width="975" height="118" alt="image" src="https://github.com/user-attachments/assets/bd72f3e6-f427-44a0-9e4b-0c571cbb9c65" />


4.	while default SSH keys are a potential security risk because they are the same for everyone, you can improve security by creating new, unique keys and backing up the old ones. 
<img width="845" height="659" alt="image" src="https://github.com/user-attachments/assets/b1edbb67-b0cb-4bee-b060-fb4646c93fa0" />
<img width="569" height="58" alt="image" src="https://github.com/user-attachments/assets/d32d0244-13a9-4ef5-9602-01f73cabb7c9" />

5.	I will be configuring the firewall on your Kali Linux system to manage network traffic and enhance security.

# CentOS VM
This document here is going to be where I will submit my notes and my process of studying for the CompTIA Linux plus exam. The material I will be studying is from Jason Dion on his Linux plus course. The course aims to cover the four domains of system management, security, Scripts containers and automation, and troubleshooting.

<img width="438" height="366" alt="image" src="https://github.com/user-attachments/assets/e84f85cb-de70-4fe8-ac8f-069eb60766da" />

Configuring the network and host name I manually added a IP address and a static IP address that will help me connect to the Internet.

<img width="598" height="372" alt="image" src="https://github.com/user-attachments/assets/6fb4de07-97f1-4125-96db-b4160ca5e124" />

For the storage partition I manually configured the various partitions for the boot sector the swap and the root.
