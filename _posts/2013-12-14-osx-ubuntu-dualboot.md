---
layout: post
title: "OSX Ubuntu Dualboot"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Dualbooting OSX and Ubuntu
==========================

This is tested on OSX 10.9 Maverick on an MacBook Pro Retina 11,1 (Late 2013)
and Ubuntu 13.10 (Saucy Salamander), all 64 bit.

1. Make room for Ubuntu by shrinking OSX partition using Disk Utility.
2. Download Ubuntu 13.10 amd64~~+mac~~ from [here](http://releases.ubuntu.com/saucy/)
    (Note: the mac-image didn't work, instead the normal amd64 image gave two menu-entries in refind - one for bios and one for efi mode).
3. Make a bootable usb drive.
4. Download [rEFInd](http://www.rodsbooks.com/refind/installing.html).
5. Install refind using `install.sh --alldrivers`.
6. Restart twice to verify the rEFInd menu appears.
7. Boot from the Ubuntu USB by holding "alt" during boot.
8. Choose "Try Ubuntu" from the boot menu.
9. Run `ubiquity -b` from a terminal and install. DON'T restart yet.
10. Find the UUID of the root partition of the newly install Ubuntu with `sudo blkid /dev/sda*`,
    or from /etc/fstab` in the new root partition..
11. Add a file `refind_linux.conf` to the boot partition of the new install and add this (replacing uuid and dev):

        "Boot with standard options" "root=/dev/sda3 ro quiet splash vt.handoff=7"  
        "Boot to single-user mode"   "root=UUID=1cd95082-bce0-494c-a290-d2e642dd82b7 ro single"  
        "Boot with minimal options"  "root=UUID=1cd95082-bce0-494c-a290-d2e642dd82b7 ro"  

    Alternatively try the `mkrlconf.sh` script that comes with refind.
12. Now restart.

*Note*:
The MacBook Pro 11,1 (and probably later ones),
seems to now support [dual bios uefi boot images](http://askubuntu.com/a/40480),
eliminating the need for the "amd64+mac" ubuntu image.
This may very well mean I could drop rEFInd and just use GRUB2,
but then I'd have to delete the existing EFI-partition,
which I dare not do before I find a report from someone else successfully doing it.

Restoring rEFInd
----------------

The refind menu can disappear after an osx update.
If this happens, just run:

    sudo bless --setBoot --folder /efi/refind --file /efi/refind/refind_x64.efi

and it should reappear on next boot. ([source](https://bbs.archlinux.org/viewtopic.php?id=165282))
However, I haven't been able to boot ubuntu after this :(

- - -
Sources:

The best instructions I could find are on
[this blog](http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html)
(which, again is based on
[this blog](http://randomtutor.blogspot.no/2013/02/installing-ubuntu-1304-on-retina.html)).

Other sources:

 - [Ubuntu wiki](https://help.ubuntu.com/community/UEFIBooting)


