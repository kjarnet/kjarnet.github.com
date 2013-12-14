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
1. Download Ubuntu 13.10 amd64+mac from [here](http://releases.ubuntu.com/saucy/).
2. Make a bootable usb drive.
3. Download [rEFInd](http://www.rodsbooks.com/refind/installing.html).
4. Install refind using `install.sh --alldrivers`.
5. Restart twice to verify the rEFInd menu appears.
6. Boot from the Ubuntu USB by holding "alt" during boot.
7. Choose "Try Ubuntu" from the boot menu.
8. Run `ubiquity -b` from a terminal and install. DON'T restart yet.
9. Find the UUID of the root partition of the newly install Ubuntu with `sudo blkid /dev/sda*`.
10. Add a file `refind_linux.conf` to the boot partition of the new install and add this (replacing uuid and dev):

        "Boot with standard options" "root=/dev/sda3 ro quiet splash vt.handoff=7"  
        "Boot to single-user mode"   "root=UUID=1cd95082-bce0-494c-a290-d2e642dd82b7 ro single"  
        "Boot with minimal options"  "root=UUID=1cd95082-bce0-494c-a290-d2e642dd82b7 ro"  

    Alternatively try the `mkrlconf.sh` script that comes with refind.
11. Now restart.

- - -
Sources:

The best instructions I could find are in
[this blog](http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html)
(which, again is based on
[this blog](http://randomtutor.blogspot.no/2013/02/installing-ubuntu-1304-on-retina.html)).

Other sources:

 - [Ubuntu wiki](https://help.ubuntu.com/community/UEFIBooting)




