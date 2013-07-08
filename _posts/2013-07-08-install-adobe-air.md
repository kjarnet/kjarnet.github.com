---
layout: post
title: "Install Adobe Air"
description: ""
category: 
tags: [AdobeAir, Wimp]
---
{% include JB/setup %}

Install Adobe Air in ubuntu 64 bit
==================================
Testet in ubuntu 13.04.

1. Download [the installer](http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin).
2. Install 32 bit libs: `sudo apt-get install ia32-libs`
3. Make installer executable: `chmod +x AdobeAIRInstaller.bin`
4. Execute installer: `./AdobeAirInstaller.bin`
5. If error about missing gnome keyring and kwallet:
    1. Find correct library-path: `locate libgnome-keyring.so`
    2. Execute installer with library-path: `LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu ./AdobeAIRInstaller.bin`
    3. Alternatively symlink the needed libraries:
    
        sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0`
        sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

    4. You should probably delete the symlinks after installing.



Sources:
---
http://askubuntu.com/a/120221
