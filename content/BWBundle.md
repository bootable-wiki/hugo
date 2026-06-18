+++
title = 'BWBundle - Pre-configured Multi-Boot System'
date = 2025-04-04T00:00:00Z
tags = ['Multi-boot', 'GRUB', 'UEFI', 'Linux']
layout = 'single'
+++


# What is BWBundle?

BWBundle packs a bootable USB system into a zip file. Just extract it to a flash drive, add [compatible ISOs](#tested-isos).  
The boot menu lists them automatically.

# Why BWBundle?

### Zero-install setup

No software to install and no administrator rights needed.  
Download the zip, extract it, and copy the files to a USB drive.  
This means you can prepare the drive from almost any device such as an iPhone or Chromebook.

### Secure Boot

Secure Boot support was the primary constraint that shaped this project.  
Uses stock Canonical-signed GRUB, the same binaries shipped with Ubuntu Linux.  
Tools like UEFI Shell, Memtest86+, and KeyTool, can be enrolled through MokManager.  
> Fedora (Red Hat's signature) and Arch (unsigned) require Secure Boot turned off for installation.  
> This does not prevent you from enabling secure boot after installation later.  
> It's just that Ubuntu's shim only really adds Ubuntu's kernel signatures to secure boot.

### Drop ISOs and boot

Place any supported ISO on the drive and it appears in the boot menu.  
If there is a newer version of a supported distribution, give it a try it may work.  
The menu uses filename patterns and will detect it automatically.  
Standalone EFI files also appear automatically (enroll through MokManager if unsigned).

### Bundled tools ready to go

BWBundle includes utilities like Memtest86+, the UEFI Shell, MokManager, and Netboot.xyz out of the box.  
These are bootable immediately, even before adding any ISO files.

### Compatible with other tools

Ventoy will always  have a larger supported ISO list and broader hardware support (MBR, 32-bit x86, ARM).  
Between issues enrolling Secure Boot keys or SBAT errors, you may still want something that boots more consistently even if the full feature set is not present.  
BWBundle is built to cohabitate on the same flash drive by using unallocated space after Ventoy's reserved partition feature.

# Requirements

- UEFI x86_64 (most computers since 2012)
- Know how to unzip files to a flash drive and have a general idea of how bootable USB drives work
- USB flash drive, 8GB or larger recommended. 
> Watch out for fakes.  
> If you cannot format a drive and need FAT32 out of the box, choose 32GB or smaller to try and guarantee it's already formatted as FAT32.

# Usage

Extact the BWBundle contents to the root of a FAT32-formatted USB drive.  
FAT32 is the most reliable format and works on all UEFI systems.  
The GRUB configurations will automatically detect and present menu entries for any matching ISO files or EFI binaries present on the drive. 

> The Rufus NTFS driver is included so you can install Windows from the same drive alongside Linux ISOs. 
> I can offer suggestions but not direct support for this setup. See [Creating Windows Installers on iPad](/ios_windows/).

# Bundled Tools

The bundle includes GRUB configuration files that provide a complete boot menu with support for multiple Linux distributions and system utilities.  
Including some of the following tools.

| Name | Purpose |
|---|---|
| MokManager | Enroll hashes of the other tools under Secure Boot |
| KeyTool | View Secure Boot keys & remove enrolled keys or hashes |
| Netboot.xyz | Boot into a variety of distros over the ethernet port |
| Memtest86+ | Test the memory of your PC |
| UEFI Shell | Basic environment to run other EFI programs, copy data, edit text files |
| Rufus Driver | NTFS / exFAT booting support, requires two partitions |
| SecureBootRecovery | Verify & install the Microsoft UEFI CA 2023 |

# Tested ISOs

BWBundle uses filename patterns to detect ISOs.  
This heuristic approach means older and future releases may also work.  
For ISOs listed with Secure Boot Disabled (⛔) you need to disable it in BIOS/UEFI.

| Distribution | Tested ISO | Secure Boot |
|---|---|---|
| Linux Mint | `linuxmint-22.3-cinnamon-64bit.iso` | ✅ |
| Linux Mint | `linuxmint-22.3-xfce-64bit.iso` | ✅ |
| Linux Mint | `linuxmint-22.3-mate-64bit.iso` | ✅ |
| Clonezilla | `clonezilla-live-20251017-questing-amd64.iso` | ✅ |
| Clonezilla | `clonezilla-live-20260220-questing-amd64.iso` | ✅ |
| Elementary OS | `elementaryos-8.1-stable-amd64.20260219.iso` | ✅ |
| KDE Neon | `neon-user-20260402-1324.iso` | ✅ |
| Zorin OS | `Zorin-OS-18-Core-64-bit-r3.iso` | ✅ |
| Rescuezilla | `rescuezilla-2.6.1-64bit.noble.iso` | ✅ |
| Ubuntu Mini | `ubuntu-mini-iso-24.04.4-mini-iso-amd64.iso` | ✅ |
| PassMark Memtest86 | 11.6 `memtest86-usb.img` | ✅ |
| Ventoy Installer | `ventoy-1.1.10-livecd.iso` | ⛔ |
| Fedora | `Fedora-Everything-netinst-x86_64-43-1.6.iso` | ⛔ |
| Fedora | `Fedora-KDE-Desktop-Live-43-1.6.x86_64.iso` | ⛔ |
| Fedora | `Fedora-Workstation-Live-43-1.6.x86_64.iso` | ⛔ |
| Arch | `archlinux-2026.04.01-x86_64.iso` | ⛔ |
| Debian | `debian-live-13.4.0-amd64-xfce.iso` | not tested yet |

# Contributions/Ways to help

Ask questions, in order to improve I need feedback, if something needs a better explanation let me know.

Finding a way to load large loopbacks on Debian builds of GRUB in Secure Boot.  
I was able to create loopbacks for gparted-live & clonezilla-live, but could not create for MXLinux or LMDE.  
I forgot the exact error but it's from GRUB trying to create a large loopback.

Debian netinst ISO not loading correctly.
