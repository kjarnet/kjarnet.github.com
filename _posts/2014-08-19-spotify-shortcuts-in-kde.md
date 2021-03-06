---
layout: post
title: "Spotify shortcuts in KDE"
description: ""
category: how-tos
tags: [kde, spotify]
---
{% include JB/setup %}

This is how you can assign a global keyboard-shortcut to play/pause spotify in KDE:

1. Open System Settings -> Custom Shortcuts.
2. Add a new Group called something like "Spotify Shortcuts".
3. Add a new Global Shortcut -> D-Bus Command.
4. Note that the group and shortcut is disabled by default.
   You need to enable it by ticking the select-box to the right of the name of the group (might need to scroll horizontally).
5. Set a Keyboard-combination in the Trigger tab (e.g. Super+Shift+F5).
6. Set the following values in the Action tab:
    * Remote application: "org.mpris.MediaPlayer2.spotify"
    * Remote object: "/org/mpris/MediaPlayer2"
    * Function: "org.mpris.MediaPlayer2.Player.PlayPause"

Sources:

* [Kubuntuforums thread](https://www.kubuntuforums.net/showthread.php?58197-How-To-Get-Global-Media-Shortcuts-in-KDE&p=303642&viewfull=1#post303642)
* [Mabishu blog post](http://www.mabishu.com/blog/2010/11/15/playing-with-d-bus-interface-of-spotify-for-linux/)

Attached an export of the Group: [spotifyremote.khotkeys](/spotifyremote.khotkeys).

