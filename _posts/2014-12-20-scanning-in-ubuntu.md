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

Converting png to pdf
---------------------

Skanlite doesn't produce pdf-files,
but it's easy to convert from png or jpg to pdf with imagemagick:

    convert input.png output.pdf

There are lots of options to convert:

* `-density 200x200` Use 200 dpi
* `-quality 60 -compress jpeg` Compress output with jpeg-compression with quality-setting of 60.

Shrinking large pdf files
-------------------------

If you have the original png-file from the scanning,
shrinking this and converting it again is probably easiest,
but if you only have the pdf,
you can try using ghostscript to shrink it:

    gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

You can increase the output quality by changing PDFSETTINGS to /ebook or /prepress (the default).

It should also be possible to shrink it with imagemagick,
by using `convert input.pdf output.pdf` with some settings of density, compression etc.,
but I've never got good results with this.

Sources: [http://askubuntu.com/a/256449/13945](http://askubuntu.com/a/256449/13945)


