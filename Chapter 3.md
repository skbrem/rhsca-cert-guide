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
| /home | Where the user's personal directories and files can be found. |
| /mnt, /media | Directories which are used for mounting devices within the system tree. |

## Mounts

Mounting is an important concept to grasp in Linux, especially when wanting to understand the overall file system. A mount is the connection between a directory and a device. The file system is shown as a single hierarchy, and `/` is the starting point. 

During the mounting process, a device is directly connected to a directory. Once the process is complete, the directory gives access to the newly-connected device. 

