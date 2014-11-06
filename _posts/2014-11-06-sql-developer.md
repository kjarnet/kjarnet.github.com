---
layout: post
title: "SQL Developer"
description: "Installing Oracle SQL Developer under Ubuntu"
category: 
tags: [sql developer]
---
{% include JB/setup %}

Tested with SQLDeveloper 4.0 on Kubuntu 14.10.

1. Download latest tarball from Oracle.
2. Unpack under a suited place, I recommend /opt.
3. Run with $INSTALL\_DIR/sqldeveloper.sh

To make a desktop-shortcut:
1. Add a file "sqldeveloper.desktop" under `~/.local/share/applications/` with the following contents:

    [Desktop Entry]
    Version=1.0
    Type=Application
    Name=Oracle SQL Developer
    Icon=/opt/sqldeveloper/icon.png
    Exec=/opt/sqldeveloper/sqldeveloper.sh
    Comment=Oracle SQL Developer
    Categories=Development;IDE;
    Terminal=true
    StartupNotify=true
    StartupWMClass=sqldeveloper

2. Run it (e.g. double-click it in your file-browser).
3. A terminal-window should pop up prompting you to enter the path to a java installation.
   This will be added to `~/.sqldeveloper/4.0.0/product.conf`
4. Edit the desktop-file and change Terminal to false to prevent the terminal to pop up every time you start SqlDeveloper.



