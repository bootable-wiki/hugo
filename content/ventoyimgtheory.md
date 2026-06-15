+++
title = 'Ventoy Theory and Quick Start'
date = 2025-03-10T03:40:00Z
tags = ['Ventoy', 'Theory', 'UEFI']
layout = 'single'
+++

## Understanding the Ventoy Layout
Ventoy uses a specific disk layout to allow for multi-boot capabilities. Usually, the drive is split into a main partition for your ISO files and a smaller EFI system partition. These pre-built disk images are mostly writing zeros to the drive as the .img format is universal and compatible across different operating systems.

## Quick Tutorial: Using Disk Images
If you do not want to use the standard Ventoy installer, you can flash a pre-built virtual hard drive image.

1. Choose an image size (256mb, 1gb, 4gb, 8gb) that fits your physical USB drive.
2. Download and extract the zip file to get the .img file.
3. Use a flashing tool like balenaEtcher or Raspberry Pi Imager to write the image to your drive.
4. Once complete, copy any ISO files directly to the visible Ventoy partition.

## Requirements
* UEFI motherboard (Standard on most computers produced after 2012).
* USB flash drive.
* A host machine (Mac, Chromebook, or Linux) to flash the image.

> Note: For 256mb images, you can use the F2 function to select ISOs from other connected drives or partitions.
