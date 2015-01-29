---
layout: post
title: "KDE Icon only task manager"
description: ""
category: how-tos
tags: [KDE, task manager, chrome]
---
{% include JB/setup %}

KDE comes with a more modern alternative to the default windows-xp-like task manager
similar to Unity's or OSX'.
It's aptly called the "Icon-only Task Manager" and you add it to the Panel
as you would any other widget (and of course remove the old task manager).

Shortcuts can be pinned to the task manager
by right-clicking the shortcut that appears when an application is running
and selecting "Show a launcher when not running".
This works for most applications, but a few (typically gtk-applications) need some tuning.
If a launcher is not working try this:

* unhook "Show a launcher..."
* Right click the task manager and select "Icon-only task manager settings".
* Select "Launcher Matching Rules" and click "+ Add".
* Click "Detect Window Properties" and then the window of the application that is not working.
* Select the launcher for the application.
* Now it should work when you select "Show a launcher when not running".

Chrome
------

Chrome in Kubuntu 14.10 has even more issues.
To make a working launcher for this,
you have to copy the global launcher to your home-catalog for some reason:

    cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/

and then you can add a "Launcher Matching Rule" as explained above.

Some additional steps I did that may have had an effect:

* In the file: ~/.kde/share/config/plasma-desktop-appletsrc,
under the section `[Containments][3][Applets][25][Configuration][Launchers]`
delete any line beginning with "Chrome=".
* Edited the google-chrome.desktop file and deleted all comments and genericNames in languages I don't use.

Sources:
______

* [https://forum.kde.org/viewtopic.php?f=67&t=118633#p297598](https://forum.kde.org/viewtopic.php?f=67&t=118633#p297598)
* [https://bugs.kde.org/show_bug.cgi?id=327948](https://bugs.kde.org/show_bug.cgi?id=327948)

