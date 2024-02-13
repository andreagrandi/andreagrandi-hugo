---
title: "The Windows Phone Emulator wasn’t able to connect to the Windows Phone operating system: how to fix it"
date: 2013-02-03
categories: 
- HowTo
- Programmazione
- Windows
- Windows Phone
slug: "the-windows-phone-emulator-wasnt-able-to-connect-to-the-windows-phone-operating-system-how-to-fix-it"
draft: false
---

This morning when I started my Windows Phone 8 emulator to test an
application, the emulator refused to work, giving me this error "**The
Windows Phone Emulator wasn’t able to connect to the Windows Phone
operating system**". Luckly it's very easy to fix. It's caused by the
virtual network interface that has been disabled for some reason
(well... in my case it must depend on the other day when I tryed to
trick WP7 firmware upgrade and used the disconnect trick, but this is
another story).

I searched on Google for a solution and I landed on this
page <http://pauliom.com/2012/12/20/the-windows-phone-emulator-wasnt-able-to-connect-to-the-windows-phone-operating-system/>

All you have to do is going to "**Network and Internet --&gt; Network
Connections**", right click on "**vEthernet (Internal Ethernet Port)
Windows Phone Emulator**" and **Enable** it.

[![network\_interface\_wp8](network_interface_wp8.png){ width=100% }](network_interface_wp8.png)

