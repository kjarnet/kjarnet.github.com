---
layout: post
title: "Installing Kubuntu on ThinkPad"
description: "Issues encountered when installing Kubuntu on my ThinkPad T440p"
category: how-tos
tags: [installing, kubuntu, thinkpad, uefi, efi]
---
{% include JB/setup %}


Installing Kubuntu on my ThinkPad T440p unfortunately was not straight forward.
Firstly, I never got it to boot from my usb 3.0 memory stick,
so had to use an older one.
Furthermore:


UEFI Trouble
------------

The efibootmgr in (K)ubuntu 14.10 appearently has some serious issues
corrupting the Boot Manager when you install it.
On the thinkpad,
this results in some recovery mechanism kicking in
on the first boot after installing Kubuntu,
and displaying the message:

"Boot Manager recover from critical error.
Some essential variables are absent or corrupted
and Boot Manager has restored them from default configuration.
Press Esc to continue or F1 to enter Setup."

And afterwards,
only windows will boot
(or if you've removed windows altogether,
nothing boots).
I suspect this is also what bricked my Dell laptop,
so be careful!

The solution seems to be
installing the efibootmgr package from 14.04:

* If you've already restarted after installation,
and can't access Kubuntu,
start from the bootable installation media.
You'll need the efiboomgr package from 14.04,
so you can either boot from a 14.04 installation media
or download it from
[http://packages.ubuntu.com/trusty/amd64/efibootmgr/download](http://packages.ubuntu.com/trusty/amd64/efibootmgr/download)
.
* Follow the steps [here](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)
to chroot and reinstall grub
with the 14.04 efibootmgr.
* Pin the version of the package before doing any apt-get update:
`sudo apt-mark hold efibootmgr`

Trackpad
--------

The trackpad behaves horribly in Kubuntu.
The best I've managed is with these settings:

* Disable tap-click
* Disable drag-lock
* Enable vertical two-finger scrolling (if you like)
* Speed: tweak this to your liking.
Sadly there are no numeric values on this,
but if we interpret the small vertical markings as whole numbers
starting at 0,
my settings are approximately:
    * Minimum: 0.8
    * Maximum: 2.9
    * Acceleration: 1.5
* Turn off pressure-dependent motion (by setting minimum and maximum factor to 1x and pressure to minimum.
* Noice cancellation: 30 units
* Sensitivity: I've got both pressure for detecting a touch and a release set to 4 (counting markings from 0).
* Palm detection: This doesn't seem to work, so I've disabled it.

Now you'll have to actually press down the trackpad to register a click,
but this is better than any alternative I've accomplished.
It's still horrible,
jumping around when I try to click
and suddenly not registering anything for a second or so.
Anyone have a better set-up, please share!

There are some related bug-reports that I haven't tried out yet:

* [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1042069](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1042069)

Note also that I've tried adding settings to a new file
`/etc/X11/xorg.conf.d/50-synaptics.conf`
which didn't make any difference,
but I've not tried changing the existing file
`/usr/share/X11/xorg.conf.d/50-synaptics.conf`.

Source:
_______

* [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1387654](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1387654)


