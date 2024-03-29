---
title: "Nokia N900: reboot loop after PR 1.1.1 upgrade is not a firmware bug"
date: 2010-02-20
categories: 
- Linux
- Maemo (EN)
- MeeGo
tags: 
- firmware
- maemo
- MeeGo
- N900
- nokia
slug: "nokia-n900-reboot-loop-after-pr-1-1-1-upgrade-is-not-a-firmware-bug"
draft: false
---

Few days ago I published [some notes]({filename}/2010/3-nokia-n900-some-problems-with-latest-pr-1-1-1-firmware.md)
about my personal experience with **PR 1.1.1** firmware upgrade in Nokia
**N900**. In particular my device got an infinite reboot loop after
upgrading the firmware and I had to flash the firmware image from
scratch to fix the problem. Today I was kindly contacted by **Max
Waterman** (I suppose he works for Nokia) and he explained me what was
the problem. It was caused by a little bug in Harmattan UI demo and they
fixed it (the fix is already available in extras-devel).

No surprise for me: extras-devel contains unstable packages and if user
enables it, he does at his own risk. The most important thing is the
fact that the official firmware without any unstable application doesn't
suffer of this problem at all. The thing that really impressed me so
much (in a positive sense) it's that I was contacted privately by a
Nokia developer apologizing for the bug (no problem man, it's part of
the game if someone want to test extras-devel software) and explaining
that they already fixed it.

This is what I like of Maemo (or should I already call it MeeGo?), I
really feel to be a part of it!

