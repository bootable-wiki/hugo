+++
title = 'Ventoy Worked Examples'
date = 2025-03-10T03:40:00Z
tags = ['macOS', 'Chromebook', 'External Drive']
layout = 'single'
+++

## Example 1: macOS Host to Create Windows 11 Installer
This method solves the issue where the Windows 11 install.wim file is larger than 4GB, preventing simple FAT32 copies.

1. Download the Windows 11 ISO from Microsoft.
2. Download the 8GB Ventoy disk image zip.
3. Extract the zip file.
4. Use Etcher to write the 8GB disk image to your flash drive.
5. Copy the entire Windows ISO file to the new Ventoy partition.
6. Connect the drive to the PC to begin installation.

## Example 2: Chromebook Host to Create Linux Installer
This is useful if your Linux desktop is corrupted and you only have a Chromebook available.

1. Download the Linux ISO (e.g., Linux Mint) to the Chromebook.
2. Download the 4GB Ventoy disk image zip.
3. Extract the zip file.
4. Open the Chromebook Recovery Utility.
5. Click "Use local image" in the utility settings and select the 4GB image.
6. Select your flash drive and write the image.
7. Copy the Linux ISO to the Ventoy partition and connect to the PC.

## Example 3: Booting from a Large External Hard Drive
Use this if you have a 1TB drive with important files and don't want to erase it, but have a spare small flash drive.

1. Download the 256MB Ventoy disk image.
2. Use balenaEtcher to put the image on a small (e.g., 512MB) USB drive.
3. Connect both the small Ventoy drive and the 1TB external drive to the computer.
4. Boot the computer from the small 512MB flash drive.
5. When the "No ISO found" message appears, press the F2 key.
6. Locate the 1TB external drive in the list and select your ISO.
