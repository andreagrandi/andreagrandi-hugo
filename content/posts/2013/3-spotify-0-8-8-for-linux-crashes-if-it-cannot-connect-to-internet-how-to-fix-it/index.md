---
title: "Spotify 0.8.8 for Linux crashes if it cannot connect to Internet: how to fix it"
date: 2013-01-06
categories: 
- HowTo
- Linux
- Ubuntu (EN)
slug: "spotify-0-8-8-for-linux-crashes-if-it-cannot-connect-to-internet-how-to-fix-it"
draft: false
---

If you upgrade Spotify for Linux to 0.8.8.x version and you have some
network connection problems (for example you're behind a company
firewall and need to set a proxy...) the application will crash/hang
without letting you doing anything (neither setting Proxy informations)

[![Screenshot from 2013-01-0618:56:15](Screenshot-from-2013-01-06-185615-300x187.png){ width=100% }](Screenshot-from-2013-01-06-185615.png)

This is caused by a deadlock in the GUI and you can view the complete
debugging informations here <http://pastebin.com/zcKgXEqz>  
To fix this, you just need to open this file
**`~/.config/spotify/prefs`** and add these two lines:

```text
network.proxy.addr="123.123.123.123:1234@https"  
network.proxy.mode=2  
```

of course substituting **`123.123.123.123:1234`** with your *proxyip:proxyport*.

