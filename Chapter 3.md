---
created: 2026-02-04
tags:
  - rhcsa
  - linux
---

## The File System Hierarchy

It's important to be familiar with the default directories that are found on almost all Linux systems. 

The layout of the directory structure in Linux is defined within the File System Hierarchy Standard, and more info about this system can be found with `man 7 file-hierarchy`.

A table breaking down the hierarchy found on most Linux systems:

| Directory | Description |
| --- | --- |
| / | This is the root directory, and the start of the file system tree. |
| /boot | This directory contains the files needed for the Linux kernel to boot. |
| /dev | Device files are foudn here, and are needed for accessing physical devices. It's needed during the boot process. |
| /etc | Configuration files found here are utilised by services and programs on the server, and it's a necessary directory for booting. |
| /home | Where the user's personal directories and files can be found. |
| /mnt, /media | Directories which are used for mounting devices within the system tree. |

## Mounts

A mount is the connection between a directory and a device. 

During the mounting process, a device is directly connected to a directory. Once the process is complete, the directory gives access to the newly-connected device. 

It's worth working with multiple mounts, as a single file system could run into issues like: 

- The file system could be filled up quickly from too much activity, bad news for a server. 
- It's bad OPSEC, where mounting allows for more granular security per mount. 
- It makes it easier to add more space to the system.

These reasons and more are why it's a good idea to split Linux file systems into different devices, including disk partitions and logical volumes. 

Certain directories are usually mounted on dedicated devices, including:

- **/boot**: Generally mounted on a different device as it contains special information that the computer needs to boot. As the `/` is commonly on an LVM (Logical Volume Manager), volume, where the OS is not able to boot by default, the kernel and other files will need to be stored elsewhere.
- **/boot/EFI**: If your PC or laptop makes use of EFI for the boot process, its own mount will be needed. 
- **/var**: 
