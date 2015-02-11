---
layout: post
title: "Scanning in ubuntu"
description: ""
category: how-tos
tags: [ubuntu, hardware, scanner, scanning, usb, pdf, shrink]
---
{% include JB/setup %}

Issues related to scanning in (K)ubuntu.

Scanner: CanoScan LiDE 25

This was not recognized by Skanlite on Kubuntu 14.10 on my new pc.

Solution: Turn off xHCI in BIOS (under USB-settings). This might mean I no longer have USB 3 support, though :(


Sources:
* [http://ubuntuforums.org/showthread.php?t=2253359](http://ubuntuforums.org/showthread.php?t=2253359)
* [Wikipedia on xHCI](https://en.wikipedia.org/wiki/Extensible_Host_Controller_Interface)


Shrinking large pdf files
-------------------------

If you have the original png-file from the scanning,
shrinking this and converting it again is probably easiest,
but if you only have the pdf,
you can try using ghostscript to shrink it:

    gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

You can increase the output quality by changing PDFSETTINGS to /ebook or /prepress (the default).

Sources: [http://askubuntu.com/a/256449/13945](http://askubuntu.com/a/256449/13945)


