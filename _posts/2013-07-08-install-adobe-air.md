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
Testet in ubuntu 13.04, 13.10

1. Download [the installer](http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin).
2. Install 32 bit libs:
    * If on ubuntu 13.04: `sudo apt-get install ia32-libs`
    * If on ubuntu 13.10: `sudo apt-get install ibus-gtk:i386 libaio1:i386 libao4:i386 libaudiofile1:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcapi20-3:i386 libcupsfilters1:i386 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libesd0:i386 libexif12:i386 libfluidsynth1:i386 libgail-common:i386 libgail18:i386 libgconf-2-4:i386 libgd3:i386 libgdbm3:i386 libgettextpo0:i386 libibus-1.0-5:i386 libieee1284-3:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libopenal1:i386 libpulse-mainloop-glib0:i386 libpulsedsp:i386 libqt4-designer:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libreadline6:i386 libsane:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libssl0.9.8:i386 libstdc++5:i386 libtdb1:i386 libunistring0:i386 libusb-0.1-4:i386 libusb-1.0-0:i386 libvorbisfile3:i386 libvpx1:i386 libwebp4:i386 libxaw7:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxtst6:i386 odbcinst1debian2:i386 xaw3dg:i386`
    (ia32-libs is removed in 13.10. Many of these libs are unnecessary - to find out which you actually need try `ldd /opt/Adobe\ Air/WiMP/bin/WiMP` and search packages.ubuntu.com for the packages containing these.
3. Make installer executable: `chmod +x AdobeAIRInstaller.bin`
4. Execute installer: `./AdobeAirInstaller.bin`
5. If error about missing gnome keyring and kwallet:
    1. Find correct library-path: `locate libgnome-keyring.so`
    2. Execute installer with library-path: `LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu ./AdobeAIRInstaller.bin`
    3. Alternatively symlink the needed libraries:
    
        sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
        sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

    4. You should probably delete the symlinks after installing.



Sources:
---
* http://askubuntu.com/a/120221
* http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package

