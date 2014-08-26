---
layout: post
title: "OSX Ubuntu Dualboot"
description: ""
category: how-tos
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

Troubleshooting
---------------

After sucessfully installing and booting Ubuntu, I installed the latest updates and then trouble started:

* Booting only worked with minimal options(?) and took for ages.
* The built-in Broadcom wifi-card didn't work, and I couldn't install the proprietary drivers.
* I finally managed to install the wifi-drivers when using a d-link usb wifi card
    but it was terribly unstable.
* The syslog was filled with lines like:

	Feb 19 22:02:18 macwonko kernel: [   96.937102] ata1.00: status: { DRDY }
	Feb 19 22:02:18 macwonko kernel: [   96.937117] ata1.00: failed command: READ FPDMA QUEUED
	Feb 19 22:02:18 macwonko kernel: [   96.937137] ata1.00: cmd 60/08:28:70:77:c3/00:00:0d:00:00/40 tag 5 ncq 4096 in
	Feb 19 22:02:18 macwonko kernel: [   96.937137]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

After googling a while, I found [this article]( https://bbs.archlinux.org/viewtopic.php?pid=1295725),
which says to add libata.force=1:noncq (where 1 is the harddrive number??) to boot parameters (grub / refind).
This fixed all of the above issues!

Still, the audio doesn't work and the touchpad is terrible :(


- - -
Sources:

The best instructions I could find are on
[this blog](http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html)
(which, again is based on
[this blog](http://randomtutor.blogspot.no/2013/02/installing-ubuntu-1304-on-retina.html)).
A lot of usefull info on [ubuntu wiki](https://help.ubuntu.com/community/MacBookPro11-1/Saucy).

Other sources:

 - [Ubuntu wiki](https://help.ubuntu.com/community/UEFIBooting)


