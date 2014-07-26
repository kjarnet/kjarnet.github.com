---
layout: post
title: "Wiping a harddrive"
description: ""
category: 
tags: []
---
{% include JB/setup %}

http://www.hirensbootcd.org/download/

http://askubuntu.com/questions/146127/how-do-i-create-a-bootable-usb-on-ubuntu-from-hirens-boot-cd-iso-for-windows

http://www.ultimatebootcd.com/download.html

http://lubuntu.net/

http://www.addictivetips.com/windows-tips/how-to-completely-wipe-erase-hard-disk-drive-step-by-step-guide/ (wipe)
http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/ (shred/wipe)

http://www.dban.org/

http://id-ten-t-error.blogspot.no/2013/03/dban-usb-unetbootin-fix.html


Also worth checking out:

    Using fsck like that may erase the data, but not irrecoverably. If you want secure deletion, use dedicated secure-erasing programs. The program "Wipe" is most likely already installed on your system, so all you have to do is use it. Assuming you are not booting from the drives (i.e. the drives are external drives and don't have an OS on them) you can clear them with the command "sudo wipe /dev/hdx". The Wipe utility may take a very long time to clear drives, but it is very secure. You could also use this with the -q flag to reduce the security slightly, but speed the process up.

    If you don't want to use Wipe for some reason, you can also use the utility Shred. To erase a drive with Shred, use "sudo shred /dev/hdx".

    Another option is the "secure-delete" package (install with "sudo apt-get install secure-delete"). It installs several utilities, but the one you'll need is called srm. To do that, use "sudo srm /dev/hdx".

    If you are very serious about security, you could also use Nwipe, which is a fork of Dwipe (the program used by the famous DBAN utility, which is another option you could use) to securely erase data. I don't think Nwipe comes installed on Ubuntu, but you can use a live CD that has Nwipe (I think PartedMagic has it). Nwipe is also extremely secure. If you do choose to use DBAN or Nwipe, the most secure configuration is to use the Gutmann method with the ISAAC algorithm as the PRNG. Nwipe took a little more than 100 hours for a 750 GB hard drive, so a 40 GB hard drive should be a lot quicker.

    The quickest (but least secure) method to overwrite a whole hard drive would be to use DD. You can either blank the hard drive with 0's using "sudo dd if=/dev/zero of=/dev/hdx" or with random data using "sudo dd if=/dev/urandom of=/dev/hdx". Note that using DD is not very secure, although it will prevent casual recovery of data.

    For more info you can look for things here.

    If you can't decide on which of these options to use, just do "sudo wipe /dev/hdx".


(http://ubuntuforums.org/showthread.php?t=2035123&p=12138631#post12138631)

http://askubuntu.com/questions/359540/securely-erase-hard-drive-using-the-disk-utility

http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive


