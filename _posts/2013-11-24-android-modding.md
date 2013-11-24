---
layout: post
title: "Android Modding"
description: ""
category: 
tags: [Android]
---
{% include JB/setup %}

Modding Android
===============

ADB and Fastboot
----------------

To install adb and fastboot on ubuntu:

  sudo apt-get install android-tools-adb
  sudo apt-get install android-tools-fastboot

Bootloader
----------

Before doing any of the following,
you need to unlock the bootloader.
...
This will wipe all data.

Fastboot mode
-------------

Press and hold volume down and power button when turning on device.
You can connect the device to your computer and use
the fastboot program to flash the nexus.
Test connectivity with `fastboot devices`.

Recovery mode
-------------

Start the device in fastboot mode and select Recovery from the menu
(using the volume buttons to toggle actions and the power-button
to execute the selected one).
You can connect the device to your compouter and use
the adb program to debug the nexus.
Test connectivity with `adb devices`.

Flash stock rom
---------------

[Nexus stock roms](https://developers.google.com/android/nexus/images).
These archives hold bootloader and system image 
as well as scripts that flash the device using fastboot.
NB: The included scripts delete all data when flashing.
To avoid this, remove the "-w" argument to the fastboot update command.

Install Clockworkmod Recovery
-----------------------------

This is an alternate/ improved recovery image
(another alternative is [Team Win Recovery Project (twrp)](http://teamw.in/project/twrp2).
 - Download from [http://www.clockworkmod.com/rommanager]
 - Install with `fastboot flash recovery your_recovery_image.img`
 - Something about stock android overwriting recovery on startup - check this.

