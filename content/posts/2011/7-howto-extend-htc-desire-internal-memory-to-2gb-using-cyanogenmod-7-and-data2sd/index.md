---
title: "HowTo extend HTC Desire internal memory to 2Gb using CyanogenMod 7 and Data2SD"
date: 2011-08-13
categories: 
- HowTo
tags: 
- Android
- Google
- Linux
- howto
- cyanogenmod
slug: "howto-extend-htc-desire-internal-memory-to-2gb-using-cyanogenmod-7-and-data2sd"
draft: false
---

[![htc-desire](htc-desire-300x260.jpg){ width=60% }](htc-desire-300x260.jpg)

## Introduction

Even if it's not a new model, the **HTC Desire** is still a very good
Android device, thanks to its **1Ghz** CPU and **512 Mb RAM**, but one
of the biggest problems of this phone is that it comes with **only
148Mb** available in the ROM. Once the operating system is installed
(ROM I mean), after installing few useful applications you'll end the
available space very soon. There are many apps available, like App2SD
that move your applications to the SD card, but it's not enough because
only the application is moved, not the data. To move the data to the SD
card, there is a very nice utility called **Data2SD**. Please note that
this procedure requires you to reflash your device and partition your SD
card, so **please do a complete backup** before proceding.

## What you need

- a **rooted** HTC Desire (you need to have a rooted phone with a **recovery** already installed)
- a **4Gb** (or bigger) **microSD**, at least **class 4** (class 6 is even better while class 10 is reported not working with this phone)
- a **microSD** card **reader**
- **CyanogenMod 7**: http://download.cyanogenmod.com/get/update-cm-7.0.3-Desire-signed.zip
- **Data2SD**: [Data2SDInstallerX1.zip](http://www.droidzone.in/roms/index.php?dir=StarBurst%2Fdata2sd%2F&download=Data2SDInstallerX1.zip) and [Data2SDReInstallerX1.zip](http://www.droidzone.in/roms/index.php?dir=StarBurst%2Fdata2sd%2F&download=Data2SDReInstallerX1.zip)
- **Google Apps**: <http://wiki.cyanogenmod.com/wiki/Latest_Version#Google_Apps>
- **GParted**: you can use the version available on Ubuntu Linux or you can download a live Linux image with GParted installed: <http://gparted.sourceforge.net/livecd.php>

## Backup your data

Before following these instructions, please **do a complete backup** of
your microSD, of your original ROM (using Nandroid or similar) ecc...

## Prepare the microSD card

- Open GParted on your Ubuntu Linux or use the GParted Live CD/USB.
- Delete all partitions on this microSD
- Create the first one using FAT32 filesystem, leaving 2Gb (**2047Mb**) available at the end.
- Create a second partition using **ext4** filesystem.
- Confirm your changes
- Copy CyanogenMod7 rom, Data2SD installers and Google Apps on FAT32 partition

## CyanogenMod 7 installation

- Reboot your phone into **Recovery** (turn it off then press volume down + power)
- **WIPE** all data (userdata, cache ecc...)
- Choose "Install from SD card" and select CyanogenMod7 installation zip
- when finished reboot your phone
- Enter your Wifi settings, language ecc.... **DO NOT enter** your Google account settings.
- reboot your phone

## Data2SD installation

- Boot into **Recovery** again
- Choose "Install from SD card" and select **Data2SDInstallerX1.zip** (please note, you may have to **turn off the signature verification** in Other-&gt;Turn off ecc...)
- when finished reboot your phone
- now you should see **1,97Gb** if you go in Settings-&gt;Storage-&gt;Internal Storage-&gt;Total space

## Google Apps installation

- Reboot your phone into Recovery
- Choose "Install from SD card" and select the Google Apps zip file
- reboot your phone

## Conclusion

You now have **1,97Gb total space available** instead of 148Mb. Enjoy your HTC Desire!

## **Update Aug 1, 2012: since December 2011 I don't have an HTC Desire anymore. These informations could be still valid but in any other case I don't have the possibility to help you more.**

