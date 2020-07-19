---
title: Ryzen HD Audio ALG892 recording workarounds on Linux
date: 2019-11-07 10:35:51
tags:
  - hardware
  - audio
---

When you record a piece of audio on an AMD Ryzen desktop with Realtek ALG892 codec running any distro of GNU/Linux, you'll find the audio distorted, high-pitch.

To workaround the problem: 
Record with bitrate higher than 48000 (default 44100).

For PulseAudio users, resampling must be disabled to keep the rate.

Edit `/etc/pulse/daemon.conf`, append:
```
resample-method = src-sinc-best-quality
default-sample-format = s16le
default-sample-rate = 88200
avoid-resampling = yes
```

Edit `/etc/pulse/default.pa`, change
`load-module module-udev-detect`
to
`load-module module-udev-detect use_ucm=0 tsched=0`

And restart PulseAudio.


P.S. Hardware and Software Configuration
* CPU: Ryzen 1700
* Mainboard: MSI B350m Mortar, with Realtek ALG892 integrated.
* OS: AOSC OS 6.0.0 "Fsck", kernel 5.3.8
* PulseAudio: 12.2-rebootstrapped
