---
title: "Alternative way to generate .deb packages for Maemo"
date: 2007-11-20
categories: 
- HowTo
- Linux
- Maemo (EN)
- Programmazione
- Ubuntu (EN)
tags: 
- debian
- maemo
- nokia
- package
slug: "alternative-way-to-generate-deb-packages-for-maemo"
draft: false
---

Thanks to **Mohammed Hassan** now I know an alternative (alternative to the [official howto](http://maemo.org/development/documentation/how-tos/4-x/creating_a_debian_package.html))
way to generate a **.deb** package for Maemo.

If the package already exist in the Debian repositories, you can get the
`.dsc` file (for example in an ftp like this:
<http://ftp.debian.org/debian/pool/non-free/s/spim/> ) and execute the
following commands:

```shell
dget -x DSC_FILE_URL
```

It will download the package and will unpack it in the current folder.
You have to enter in the created folder and edit the debian/* files to
personalize settings, mantainer data, add deps ecc...

When you're done, you can generate the package with the usual command:

```shell
dpkg-buildpackage -rfakeroot

