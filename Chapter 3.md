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
- **/var**: Commonly on a dedicated device because it's able to expand dynamically in size. 
- **/home**: Kept on a dedicated device to ensure good security. It's possible to mount it with certain options like `noexec` and `nodec` which helps to better security. It's advantageous to have home directories in a separate file system when installing in order to make sure they survive the reinstallation of the system.
- **/usr**: Contains files for the operating system, and users normally do not need write access to this. It's a good idea to put this on a dedicated device which allows admins to configure this as a read-only mount.

It's common to find servers that have other directories mounted on partitions or volumes, and is usually up to what the admin feels is best. 

### An Overview of Mount Points and Devices

Use the `mount` command to get an overview of all the mounted devices on the system. The `/proc/mounts` file is read to get the necessary information, and will show kernel interfaces too, leading to a large list of mounted devices. 

Reading available disk space on mounted devices can be done with the `df -Th command`, and is helpful to get an overview of all the file systems that are mounted. Using the `-h` option makes it human readable, and the `-T` option shows which file system type is used for the various mounts. 

