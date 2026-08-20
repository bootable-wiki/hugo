+++
title = 'BWBundle - Multi-Boot USB System'
date = 2025-04-04T00:00:00Z
tags = ['Multi-boot', 'GRUB', 'UEFI', 'Linux']
layout = 'single'
+++

# What is BWBundle?

BWBundle provides a bootable USB system in a zip file. Extract the zip to a USB drive. Add [compatible ISO files](#tested-isos). The boot menu lists the ISOs automatically.

# Why BWBundle?

### Zero-install setup

You do not need to install software. You do not need administrator rights. Download the zip file. Extract it to a USB drive. Copy the files to the USB drive. You can prepare the drive from many devices, for example, an iPhone or a Chromebook.

### Secure Boot

Secure Boot support was the main reason for this project. BWBundle uses stock Canonical-signed GRUB. These are the same binaries that Ubuntu Linux ships. Use MokManager to enroll tools such as UEFI Shell, Memtest86+, and KeyTool.

> Fedora (Red Hat's signature) and Arch (unsigned) need Secure Boot disabled for installation.
> You can enable Secure Boot after installation.
> Secure Boot with the Ubuntu shim accepts only Ubuntu kernel signatures.

### Drop ISOs and boot

Place a supported ISO file on the USB drive. The boot menu shows the ISO automatically. If a newer version of a distribution is available, try it. It may work. The menu uses filename patterns to detect ISOs. Standalone EFI files also appear automatically. Enroll unsigned EFI files through MokManager.

### Bundled tools ready to use

BWBundle includes Memtest86+, the UEFI Shell, MokManager, and Netboot.xyz. You can boot these tools immediately, even before you add ISO files.

### Compatible with other tools

Ventoy has a larger list of supported ISOs and supports more hardware (MBR, 32-bit x86, ARM). Ventoy can have issues with Secure Boot key enrollment and SBAT errors. You may want a tool that boots more consistently even with fewer features. BWBundle can coexist on the same USB drive with Ventoy.

Ventoy can [reserve unallocated space](https://ventoy.net/en/doc_disk_layout.html#reserve_space) at the end of the drive. BWBundle can use this unallocated space if formatted to FAT32. You can have both tools on one USB drive. Carry each tool on a separate USB drive if you prefer.

# Requirements

- A computer with UEFI x86_64 (most computers from 2012 or later)
- Know how to unzip files to a USB drive. Know how bootable USB drives work.
- A USB drive. Choose a drive size based on the ISO files you want to store.

> Watch out for fake USB drives.
> FAT32 is common on USB drives smaller or equal to 32 GB. You can copy these files to a USB drive that already has content. If the extractor asks about the EFI folder, choose to overwrite all files.

# Usage

Extract the BWBundle contents to the root of a FAT32 USB drive. FAT32 works on all UEFI systems. The GRUB configurations detect ISO files and EFI binaries on the USB drive. The boot menu shows entries for each match.

> BWBundle includes the Rufus NTFS driver. You can install Windows from the same USB drive as Linux ISOs.
> BWBundle offers suggestions only. It does not provide direct support. See [Creating Windows Installers on iPad](/ios_windows/) for more information.

# Bundled Tools

The bundle includes GRUB configuration files. These files create a boot menu for multiple Linux distributions and system utilities. The bundle includes the following tools:

| Name | Purpose |
|---|---|
| MokManager | Enroll hashes of the other tools under Secure Boot |
| KeyTool | View Secure Boot keys and remove enrolled keys or hashes |
| Netboot.xyz | Boot into distributions over the ethernet port |
| Memtest86+ | Test the memory of the computer |
| UEFI Shell | DOS style interface to boot other EFI applications |
| Rufus Driver | NTFS and exFAT boot support, requires two partitions |
| SecureBootRecovery | Verify and install the Windows UEFI CA 2023 |

# Tested ISOs

BWBundle uses filename patterns to detect ISOs. This pattern-based approach means older and future releases may also work. For ISOs listed with Secure Boot Disabled (N), disable Secure Boot in BIOS or UEFI.

[Download Linux Mint](https://dl.bootable.wiki/mint-iso)

| Distribution | Tested ISO | Secure Boot |
|---|---|---|
| Linux Mint | `linuxmint-22.3-cinnamon-64bit.iso` | Y |
| Linux Mint | `linuxmint-22.3-xfce-64bit.iso` | Y |
| Linux Mint | `linuxmint-22.3-mate-64bit.iso` | Y |
| Clonezilla | `clonezilla-live-20251017-questing-amd64.iso` | Y |
| Clonezilla | `clonezilla-live-20260220-questing-amd64.iso` | Y |
| Elementary OS | `elementaryos-8.1-stable-amd64.20260219.iso` | Y |
| KDE Neon | `neon-user-20260402-1324.iso` | Y |
| Zorin OS | `Zorin-OS-18-Core-64-bit-r3.iso` | Y |
| Rescuezilla | `rescuezilla-2.6.1-64bit.noble.iso` | Y |
| Ubuntu Mini | `ubuntu-mini-iso-24.04.4-mini-iso-amd64.iso` | Y |
| PassMark Memtest86 | 11.6 `memtest86-usb.img` | Y |
| Ventoy Installer | `ventoy-1.1.10-livecd.iso` | N |
| Fedora | `Fedora-Everything-netinst-x86_64-43-1.6.iso` | N |
| Fedora | `Fedora-KDE-Desktop-Live-43-1.6.x86_64.iso` | N |
| Fedora | `Fedora-Workstation-Live-43-1.6.x86_64.iso` | N |
| Arch | `archlinux-2026.04.01-x86_64.iso` | N |

# Contributions

Ask questions on [GitHub](https://github.com/bootable-wiki/bwbundle/issues). BWBundle needs feedback to improve. If something needs a better explanation, let the maintainers know.

Find a way to load large loopbacks on Debian builds of GRUB in Secure Boot. Loopbacks work for gparted-live and clonezilla-live. Loopbacks do not work for MXLinux or LMDE. The exact error is from GRUB when it tries to create a large loopback. The Debian netinst ISO does not load correctly.
