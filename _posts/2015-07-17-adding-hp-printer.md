---
layout: post
title: "Adding HP Printer"
description: "Installing HP LaserJet P1005 under ubuntu"
category: how-tos
tags: [printer, hp, laserjet, p1005, hplip, hardware, ubuntu, plugin]
---
{% include JB/setup %}

Sometimes the open driver works well,
but it seems the hplip driver is more stable.
The hplip driver for HP LaserJet P1005 needs a proprietary plugin,
that you need to download first.
This can be done via hplip-gui,
but last time I tried I got an error
stating that the checksum didn't match
for the downloaded plugin.
The solution was then to:

    * Uninstall the printer
    * Purge and reinstall hplip (may have been unnessecary).
    * Download the plugin from [openprinting.org](https://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/).
        * Download the file called 'hplip-x.xx.xx-plugin.run',
        where you replace the x-s with the hplip installed version.
    * Reinstall the printer with `sudo hp-setup`
    * When asked for a plugin, choose the one you downloaded.
    * The printer should make some noises, and should now work :)

Sources: 
- - -

* [http://ubuntuforums.org/showthread.php?t=2178303](http://ubuntuforums.org/showthread.php?t=2178303)
* [http://ubuntuforums.org/showthread.php?t=1362925](http://ubuntuforums.org/showthread.php?t=1362925)



