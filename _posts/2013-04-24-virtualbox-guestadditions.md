---
layout: post
title: "Virtualbox Setup"
description: "Some gotchas I've encountered when setting up a vm in Virtualbox"
category: how-tos
tags: [virtualbox]
---
{% include JB/setup %}

Terminology
-----------
* Host: The physical pc running virtualbox manager
* Guest: The virtual machine

Virtualbox Guest-additions
--------------------------
These are required for features such as
shared folders, shared clipboard and (in windows) video-drivers.
They are installed on the guest.

### Ubuntu
(tested on 12.04 amd64)   
The version of theguest-additions in the official repos (4.1.x) 
doesn't work - you need > 4.2.
If you've installed virtualbox on the host
using oracles repo (or downloaded binaries)
you can install the guest-additions on the guest 
by following these instructions:

* Install dependencies:
`sudo apt-get install dkms build-essential linux-headers-generic`(?)
* Go to "Install guest additions" in the Devices menu
of the guest virtualbox window (Hostbutton+D).
* Mount the cdrom: `sudo mount /dev/cdrom /media/cdrom`
* Run the VboxAdditions(?) shell command:
`cd /media/cdrom && sudo sh VboxAdditions`

### Windows
Do essentially the same thing as on ubuntu,
but cdrom is of course mounted automatically.


