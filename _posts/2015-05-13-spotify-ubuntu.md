---
layout: post
title: "Spotify Ubuntu"
description: "Installing Spotify in (K)Ubuntu"
category: how-tos
tags: [spotify]
---
{% include JB/setup %}

Tested in Kubuntu 15.04 and 15.10

Spotify has an official client developed in qt, available via repo:

1. Add this line to your list of repositories by editing your `/etc/apt/sources.list`

        deb http://repository.spotify.com stable non-free

2. If you want to verify the downloaded packages, you will need to add our public key

        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 94558F59

3. Run apt-get update

        sudo apt-get update

4. Install spotify!

        sudo apt-get install spotify-client

However, this depends on libgcrypt11, which in ubuntu 15.04 and 15.10 is replaced by libgcrypt20.
If you try to run spotify, you'll get the following error message:

    spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory

To solve this, we have to manually download and install libgcrypt11 deb-file.
It can be found here: [https://launchpad.net/ubuntu/+source/libgcrypt11](https://launchpad.net/ubuntu/+source/libgcrypt11)
and installed by double-clicking, or `dpkg -i libgcrypt11_1.5.4-2ubuntu1.1_amd64.deb` (replace with your version).

______

Sources:

* [https://www.spotify.com/no/download/previews/](https://www.spotify.com/no/download/previews/)
* [http://www.webupd8.org/2015/04/fix-missing-libgcrypt11-causing-spotify.html](http://www.webupd8.org/2015/04/fix-missing-libgcrypt11-causing-spotify.html)

