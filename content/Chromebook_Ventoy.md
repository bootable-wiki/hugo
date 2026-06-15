+++
title = 'Chromebook Ventoy'
layout = 'single'
tags = ['Chromebook', 'UEFI', 'Ventoy']
+++

# Requirements
- UEFI-compatible PC (Target machine).
- USB flash drive (64GB recommended).
- A Chromebook.
> Note: If using an Enterprise or school-managed Chromebook, certain extensions or methods may be restricted.

## 1. Prepare the Ventoy Image
Because Chromebooks cannot natively burn ISO files to USB, we use a workaround via the Chrome Recovery Utility.
- Download the Ventoy livecd.ISO from the [Ventoy GitHub releases page](https://github.com/ventoy/ventoy/releases).
- Open the Files app.
- Right-click the ISO file and select Rename.
- Add .bin to the end of the filename (e.g., ventoy.iso.bin) so the recovery utility can recognize it.

## 2. Flash the Drive
- Install the [Chromebook Recovery Utility](https://chromewebstore.google.com/detail/chromebook-recovery-utili/pocpnlppkickjfloemnnooapiabbeidg) from the Chrome Web Store.
- Open the utility and click the Gear icon in the top right.
- Select Use local image.
- Choose the .bin file you just renamed.
- Select your USB flash drive and click Continue.
- Once finished, the drive is now a "Ventoy Live CD".

## 3. Convert to Full Ventoy Disk
The drive at this stage is read-only and requires a secondary step on a PC to become fully functional.
- Plug the drive into a PC and boot from the USB (typically F12 for Lenovo/Dell).
- Select the EFI USB Device from the boot menu.
- Once the Ventoy environment loads, select the Ventoy Installer option.
- Ensure MBR is selected for maximum compatibility.
- Click Install. This will erase the drive and format it with the full Ventoy structure.
- When you see "Success," you can unplug the drive and return to your Chromebook.

## 4. Add ISOs
- Plug the drive back into the Chromebook.
- You will see a partition named Ventoy.
- Simply copy your Windows or Linux ISOs and paste them directly onto this partition.