---
title: "How to configure an Ethernet connection between iPad and RaspberryPi through USB-C"
date: 2024-10-26
categories: 
- Howto
tags:
- tutorial
- hwoto
- raspberrypi
- ethernet
- usbc
- connection
- iPad
- configuration
slug: "howto-configure-ethernet-connection-ipad-raspberrypi-usbc"
description: "This tutorial explains how to configure an Ethernet connection between an iPad and a RaspberryPi using the USB-C port."
---

I recently found out (thanks to [this article](https://hamatti.org/posts/my-on-the-go-solution-with-ipad-and-raspberry-pi/) from **Juha-Matti Santala**) that not only **you can power a RaspberryPi device through the USB-C** of an iPad but that you can also **get an ethernet connection** through it

## Requirements

- an **USB-C iPad** (I used an iPad Air 4th gen)
- a **USB-C cable** (I used the one that comes with the iPad)
- a **RaspberryPi** (you need at least a RPI 4. I used a RPi 5)
- you already have **SSH access to the RaspberryPi** (I won't cover this part in this tutorial)
- an updated bootloader on the RaspberryPi (check [this documentation](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#update-the-bootloader))

## Configuration

1. Connect to the RaspberryPi using SSH
2. Become **super user** on the RaspberryPi: `sudo su`
3. Edit `/boot/firmware/cmdline.txt` and add these options **after `rootwait`**:
```text
modules-load=dwc2,g_ether
```
4. Edit `/boot/firmware/config.txt` and make sure that `otg_mode=1` is **uncommented**. 
Then add this line after the `[all]` section:
```text
dtoverlay=dwc2
```
5. Use this command to add a new connection:
```text
nmcli con add type ethernet con-name ethernet-usb0
```
6. Edit `/etc/NetworkManager/system-connections/ethernet-usb0.nmconnection` and make sure you have these settings:
```text
[connection]
id=ethernet-usb0
uuid=<random group of characters here>
type=ethernet
autoconnect=true
interface-name=usb0
  
[ethernet]
  
[ipv4]
method=shared
  
[ipv6]
addr-gen-mode=default
method=auto
  
[proxy]
```
7. Edit `/usr/local/sbin/usb-gadget.sh` and add this:
```text
#!/bin/bash

nmcli con up ethernet-usb0
```
8. Make the file executable:
```text
chmod a+rx /usr/local/sbin/usb-gadget.sh
```
9. Edit `/lib/systemd/system/usbgadget.service` and add this:
```text
[Unit]
Description=My USB gadget
After=NetworkManager.service
Wants=NetworkManager.service
  
[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/local/sbin/usb-gadget.sh
  
[Install]
WantedBy=sysinit.target
```
10. Enable the service using this command:
```text
systemctl enable usbgadget.service
```
11. Reboot the RaspberryPi:
```text
reboot
```

## Check the configuration is working

Connect the RaspberryPi to the iPad using the USB-C cable and wait for it to boot. Once it finishes booting up, open **Settings**
on the iPad and check if there is an **Ethernet** section below the **WiFi Connection**. If you find the entry, then it means the connection is successful.

## References

This tutorial has been written thanks to this other tutorial https://github.com/verxion/RaspberryPi/blob/main/Pi5-ethernet-and-power-over-usbc.md
