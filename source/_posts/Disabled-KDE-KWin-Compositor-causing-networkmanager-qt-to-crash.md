---
title: Disabled KDE/KWin Compositor causing networkmanager-qt to crash
date: 2026-03-19 14:52:14
tags: tech, linux
---

Behavior: Connect to a VPN, networkmanager-qt crashes, causing plasmashell to dump core and restart.
Workaround: Enable KWin Composite in KDE System Settings.

networkmanager-qt 5.115.0, kwin 5.27.12, AOSC OS 13.1.4
