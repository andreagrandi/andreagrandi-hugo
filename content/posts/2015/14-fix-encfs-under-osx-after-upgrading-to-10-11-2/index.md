---
title: "Fix encfs under OSX after upgrading to 10.11.2"
date: 2015-12-09
categories: 
- HowTo
- OSX
tags: 
- bug
- encfs
- security
slug: "fix-encfs-under-osx-after-upgrading-to-10-11-2"
draft: false
---

After having upgraded **OSX** to **10.11.2** on my MacBook, I noticed
that my **encfs** volume didn't mount after reboot. I tried to run the
script manually and all I got was this error:

```shell
dyld: Symbol not found: __ZN5boost7archive17xml_iarchive_implINS0_12xml_iarchiveEE13load_overrideERNS0_15class_name_typeEi
  Referenced from: /usr/local/Cellar/encfs/1.8.1/lib/libencfs.6.dylib
  Expected in: /usr/local/lib/libboost_serialization-mt.dylib
in /usr/local/Cellar/encfs/1.8.1/lib/libencfs.6.dylib
```

I quickly found that was a common problem caused by a new version of
**Boost** being
installed: <https://github.com/Homebrew/homebrew/issues/46254>

To fix it, you just need to **reinstall encfs** using this command

```shell
brew reinstall -s encfs

