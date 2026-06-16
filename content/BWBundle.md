+++
title = 'BWBundle - Pre-configured Multi-Boot System'
date = 2025-04-04T00:00:00Z
tags = ['Multi-boot', 'GRUB', 'UEFI', 'Linux']
layout = 'single'
+++


## What is BWBundle?

BWBundle is a pre-configured multi-boot system designed to simplify the process of creating bootable USB drives. It combines GRUB2 configurations and essential EFI tools into a ready-to-use package. ISO files are not included and must be downloaded separately.

## Contents

The bundle includes GRUB configuration files that provide a complete boot menu with support for multiple Linux distributions and system utilities. Including some of the following tools.

| Name | Purpose |
|---|---|
| MokManager | Enroll hashes of the other tools under Secure Boot |
| KeyTool | View Secure Boot keys & remove enrolled keys or hashes |
| Netboot.xyz | Boot into a variety of distros over the ethernet port |
| Memtest86+ | Test the memory of your PC |
| UEFI Shell | Basic environment to run other EFI programs, copy data, edit text files |
| Rufus Driver | NTFS / exFAT booting support, requires two partitions |
| SecureBootRecovery | Verify & install the Microsoft UEFI CA 2023 |

## Tested ISOs

BWBundle uses filename patterns to detect ISOs. This heuristic approach means older and future releases may also work. For ISOs listed with Secure Boot Disabled (⛔) you need to disable it in BIOS/UEFI.

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

## Key Features

BWBundle uses glob patterns to automatically detect ISO files and EFI binaries, provides clear warnings when tools require Secure Boot to be disabled, and offers multiple boot modes including standard, compatibility, and RAM-boot options. A built-in system information menu displays CPU, motherboard, BIOS, and Secure Boot status. MokManager is included for enrolling unsigned EFI binaries when Secure Boot is enabled.

## Requirements

UEFI motherboard (Secure Boot may need to be disabled for some tools), USB flash drive (8GB+ recommended for full functionality), and basic understanding of GRUB and EFI booting.

## Usage

Copy the BWBundle contents to the root of a FAT32-formatted USB drive. The GRUB configurations will automatically detect and present menu entries for any matching ISO files or EFI binaries present on the drive.

## Contributions/Ways to help

Ask questions, in order to improve I need feedback, if something needs a better explanation let me know.

Finding a way to load large loopbacks on Debian builds of GRUB in Secure Boot. I was able to create loopbacks for gparted-live & clonezilla-live, but could not create for MXLinux or LMDE. I forgot the exact error but it's from GRUB trying to create a large loopback.

Debian netinst ISO not loading correctly.
