+++
title = 'Creating Windows Installers on iPad'
layout = 'single'
tags = ['iPadOS', 'UEFI', 'Windows', 'Diskpart']
+++

# Requirements
- UEFI motherboard.
- USB-C iPad OR a Lightning iPad with a [USB 3 Camera Adapter](https://www.apple.com/shop/product/MK0W2AM/A/lightning-to-usb-3-camera-adapter).
- USB Flash Drive.
- Windows 11 ISO.

## 1. Format the Drive to FAT32
For the motherboard to recognize the initial boot files, the drive must use the FAT32 file system.
- Open the Files app.
- On iPadOS, choose MS-DOS (FAT).
- Verify the format is correct; it should be completely empty.

## 2. Prepare the Initial Files
Standard FAT32 partitions cannot hold files larger than 4GB, which means the 5GB install.wim file in the Windows ISO cannot be stored.
- Download [BWBundle](/bwbundle/) (zip) or the [UEFI NTFS driver](https://github.com/pbatard/rufus/blob/master/res/uefi/uefi-ntfs.img) (img) (from Rufus).
- Extract all files from the Windows ISO to the USB drive EXCEPT for install.wim.
- This creates a "light" installer capable of booting into a command prompt.

## 3. Partitioning via Diskpart
Boot the "light" installer on your PC and press Shift + F10 to open the Command Prompt.
- Type diskpart to start the partition tool.
- Select your USB drive (be extremely careful to choose the correct disk by size).
- Use clean to erase the drive.
- Create two partitions:
    1. A small 100MB FAT16 partition for the UEFI driver.
    2. A large exFAT partition for the full Windows installer files.
- Format the exFAT partition: format fs=exfat.
- Format the FAT partition: format fs=fat.

## 4. Final Setup and Booting
- Copy the UEFI NTFS driver to the small FAT partition.
- Copy the entire contents of the Windows ISO (including the large install.wim) to the exFAT partition.
- Disable Secure Boot in your PC's BIOS/UEFI settings, as third-party drivers are not signed by Microsoft.
- Boot from the USB drive. The motherboard will load the driver from the FAT partition, allowing it to see the exFAT partition and launch the full Windows installer.

> Note: You may need to use regedit during installation to bypass TPM or Secure Boot requirements if your hardware is older.