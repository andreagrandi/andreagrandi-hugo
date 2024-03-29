---
title: "The UNOFFICIAL way to get Os2008 into Nokia N800"
date: 2007-11-16
categories: 
- HowTo
- Linux
- Maemo (EN)
tags: 
- maemo
- nokia
- os2008
slug: "the-unofficial-way-to-get-os2008-into-nokia-n800"
draft: false
---

Since **Os2008** for **N810** is out, a lot of people were asking
about the possibility to install it on their **N800**. Nokia will relase Os2008 for N800
too, but at the moment they don't offer the possibility to download it
since the N810 firmware it's **not 100% compatible** with the old N800.

The only way to download a Nokia tablet firmware is being the owner of a
tablet. The user has to enter it's own MAC-address to be able to
download the file. To download a N810 firmware you need to have a valid
N810 MAC-address.

A [post](http://www.news.com/8301-10784_3-9816300-7.html?tag=nefd.only)
on News.com describes the exact procedure to follow if you want to try
this in your N800:

- Go to the [N810 software download
page](http://tablets-dev.nokia.com/nokia_N810.php){.external-link}.```

- Enter the serial number for a valid N810 device. To get one of
these, pick any number between `001d6e9c0000` to `001d6e9cffff`.
Pick any random 4 digits (between 0-9 and a-f hex) as the last 4
digits.```

- Download the file named **RX-44_2008SE_1.2007.42-18_PR_COMBINED_MR0_ARM.bin**
- Download the latest [firmware-upgrading software, "flasher-3.0"](http://tablets-dev.nokia.com/d3.php?f=flasher-3.0).
- Now that you have the firmware flasher and the 2008 N800 software update in the same directory, open up a terminal (on a Linux
desktop/laptop), and type:

- `chmod a+x ./flasher-3.0`
- `./flasher-3.0 -u -F RX-44_2008SE_1.2007.42-18_PR_COMBINED_MR0_ARM.bin`
```

- That will unpack the software, and it may take a few seconds. Once
that is done, plug the N800 into your computer, using the included
USB cable, then reboot the Nokia device while holding the home
button. Now execute the following commands:

- `sudo ./flasher-3.0 --enable-rd-mode`
- `sudo ./flasher-3.0 -k zImage -f`
- `sudo ./flasher-3.0 -n initfs.jffs2 -f`
- `sudo ./flasher-3.0 -r rootfs.jffs2 -f -R`
```

- That should be it. Your device should now boot up with the new 2008
version of the Nokia Maemo operating system.
```

**Note:** Nokia **DOESN'T SUPPORT** this procedure in ANY way. You can
follow this procedure at your own risk. Neither me or Nokia have the
responsability of any damage caused to your device.

