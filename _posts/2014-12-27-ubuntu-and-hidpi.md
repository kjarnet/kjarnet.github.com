---
layout: post
title: "Ubuntu and HiDPI"
description: ""
category: how-tos
tags: [ubuntu, hidpi]
---
{% include JB/setup %}

Tips for making ubuntu usable on a HiDPI screen.

# Unity
Unity has good HiDPI support, with a zoom-level found under screen settings.

Due to some bug (?) Nautilus (the file-browser) is not affected by the set zoom-level after login,
(perhaps because Nautilus starts up early in the login-process and runs in the background).
Quitting nautilus with `nautilus -q` fixes the problem,
so I made a script with only this line and made it run on login by adding it to Autostart (search in dash).

# KDE
KDE also has quite good HiDPI support.
The easiest here seems to be to set "Force font dpi" to a higher value (normal is 96, 180 is a nice value).
This is located under System Settings -> Application Appearance -> Fonts. 
Under Icons -> Advanced in the same dialog, you can upsize the all icons as well.

# Applications

## Firefox

In about:config, set layout.css.devPixelsPerPx to required zoom level.

## Chrome/Chromium

Start chrome with `google-chrome --force-device-scale-factor=1.5`.
This can be added to Exec-line in the google-chrome/ chromium-browser .desktop-file
located under /usr/share/applications.

______

Sources:

* http://askubuntu.com/questions/532988/font-problem-in-nautilus-with-hidpi
* https://wiki.archlinux.org/index.php/HiDPI






