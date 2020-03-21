---
layout: post
title: "Installing Ubuntu on MacBook 2.1"
categories:
  - Old Computer
tags:
  - macbook
  - ubuntu
  - linux
---

Installing Ubuntu from a live USB on a Macbook 2.1 is quite difficult.
Here are my attempts.

## 1. Introduction
The Mabook 2.1 serie is difficult to deal with because of the *Unified 
Extensible Firmware Interface*, ([UEFI](https://doc.ubuntu-fr.org/uefi))
 of the computer. It is in 32bits, and the CPU is a 64bits one. 
 Therefore, there are two choices:
 - Installing the 32 bits version of Lubuntu, and not using the computer
 at its maximum performance. (**to check** : One advantage is to be able to install Lubuntu 
 alongside other EFI systems.)
 ([installing Ubuntu in EFI mode](https://doc.ubuntu-fr.org/uefi)).
 - Installing a 64 bits version of Lubuntu, and finding a workaround for the UEFI.


## 2. Standard Lubuntu install
To perform the installation of Lubuntu on a Macbook 2.1, the following steps
 are necessary:
 - Preparing the boot media,
 - booting on it,
 - installing the system.
 
### 2.a. Preparation of the Lubuntu CD and boot
Booting from a CD or DVD seems the easiest way to boot on Live Ubuntu.
No blank DVDs were available at the time of the install. So burning a CD 
with an alternate iso 
(see [Ubuntu wiki](https://doc.ubuntu-fr.org/installation_alternate) 
for more information) could do the trick. But, the alternate iso of 
Lubuntu 18.04 is 717 Mo large, too much for a CD.

Booting from a mini.iso (see 
[Lubuntu minimal install](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
for more information) burned on a CD doesn't work either. 
A strange prompt is displayed with two numbered items without 
description:
```
1.
2.
Select CD-ROM boot option: |
```

According to [this article](https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)
the Macbook isn't able to read multi-catalog disk image. A 
multi-catalog disk image allows a linux distro to boot either 
in BIOS or EFI mode. By changing the disk image to be BIOS only, the Macbook 
is able to boot on it.

It is straightforward to fix a mini.iso using the proposed program
 and then to burn it on a CD for an install on Macbook 2.1.

The CD appears on the boot menu when the `option` key is pressed. Using 
the `c` key doesn't work.

### 2.b. Installation using the *mini.iso*
Installing with the minimal iso is more difficult than with standard 
install. But by following the [wiki](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Install_.2813.10_and_later.29)
 It is fairly easy. Nonetheless, two things are not so easy to deal with:
- If a GUID Partition Table (GPT) is used, one EFI partition of about
 500Mo must be created. Once created in the free space, the option 
 EFI Partition System must be selected. For manual partitioning see this [wiki](https://help.ubuntu.com/community/DiskSpace).
- At the end of the installation, the installer asks for extra package.
Be sure to select the wanted package (like `lubuntu-desktop`) with the 
`space bar` before hitting the `enter` key. If this step is forgotten,
 then after the first boot make a `sudo apt-get install lubuntu-desktop` 
to add the desktop.

### 2.c. Side notes about the installation
Using an old CD of Ubuntu 11.04, the Macbook was able to boot 
on Live Ubuntu. One can upgrade the system to the wanted version, but 
as stated [here](https://forum.ubuntu-fr.org/viewtopic.php?id=1566641)
 this method is not practical. Indeed the upgrader can only install 
 the above version (for example 11.10 upgrade for a 11.04 system).
Upgrading from an unsupported version of Ubuntu is not easy since 
the servers are not available anymore.

### 2.d. Other options
German website with specific instruction to build a live image of Linux for this specific Mac era [mesom.de](https://mesom.de/efi32boot/index.html)

Informations for grub boot options (`nomodeset`, `acpi=off`, `noapic`, `nolapic`...) :    
[ask ubuntu Grub Option](https://askubuntu.com/questions/716957/what-do-the-nomodeset-quiet-and-splash-kernel-parameters-mean)

## 3. Tweaking the system for the Macbook
The standard installation of Lubuntu performs well on a Macbook 2.1, but
some tweaks are necessary to use it at its maximum.

### 3.a. Graphics drivers
The Macbook 2.1 serie doesn't use a graphic card but a chipset, and 
more precisely the Intel GMA 945, OpenGL 1.4 hardware compatible chipset.
By default in Lubuntu, the ppa `graphics-drivers` provides open-source
drivers for graphic chipset. But Oibaf ppa 
([oibaf/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers))
 provides up to date open-source graphics drivers and option to use 
software renderer OpenGL for old hardware.

To run an OpenGL program (in this case glxgears -info) with gallium llvmpipe software render:
```bash
$ LIBGL_ALWAYS_SOFTWARE=1 glxgears -info
```

The following softwares run successfully with this option:    
| Softwares            | test |    
|----------------------|------|    
| Blender 2.79         | 1    |
| FreeCAD 0.18.3       |  2   |
| Ultimaker Cura 4.2.1 |  3   |




### 3.b. Official Mactel support page

[https://wiki.ubuntu.com/IntelMacSupport](https://wiki.ubuntu.com/IntelMacSupport)
[https://wiki.debian.org/MacBook](https://wiki.debian.org/MacBook)

### 3.c. Icon theme
The new Papirus theme used in Lubuntu is really nice.
To install it, go to [https://github.com/PapirusDevelopmentTeam/papirus-icon-theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme).