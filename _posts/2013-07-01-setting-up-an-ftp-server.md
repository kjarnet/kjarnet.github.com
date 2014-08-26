---
layout: post
title: "Setting up an FTP server"
description: "Setting up a secure FTP server on ubuntu"
category: how-tos
tags: [ftp, ubuntu 13.04]
---
{% include JB/setup %}

Install vsftpd: `sudo apt-get install vsftpd`

Add a safe ftp-user (seems to need an actual shell,
even though most tutorials recommend setting `-s /bin/false`:

    sudo useradd ftpuser -d /home/ftpuser -s /bin/bash
    sudo passwd ftpuser

Create download and upload-directories, as, because of some security issue,
the root shared directory shouldn't be writable.

    sudo mkdir /home/ftpuser
    cd /home/ftpuser
    sudo mkdir download upload
    sudo chown -R ftpuser:ftpuser .
    sudo chmod 550 download
    sudo chmod 550 .

Configure `/etc/vsftpd.conf` to allow only ftpuser to log in
and jail (chroot) him in pub directory.

    anonymous_enable=NO
    local_enable=YES
    write_enable=YES
    userlist_deny=NO
    userlist_enable=YES
    userlist_file=/etc/vsftpd.allowed_users
    chroot_local_user=YES
    chroot_list_enable=NO

Then add the line `ftpuser` to `/etc/vsftpd.allowed_users`
and restart vsftpd: `sudo service vsftpd restart`.

The port will be 21 (even though one line says `connect_from_port_20=YES`).
Download folder will be accessible as `/download` and upload as `/upload`.

Sources:

- - -

* [thread on proftpd](http://ubuntuforums.org/showthread.php?t=79588)
* [Nice tutorial on arch wiki](https://wiki.archlinux.org/index.php/Very_Secure_FTP_Daemon)
* [Ubuntus community wiki](https://help.ubuntu.com/community/vsftpd)
* [Full man page](http://vsftpd.beasts.org/vsftpd_conf.html)
* [Thread about login shell](http://ubuntuforums.org/showthread.php?t=1961286)

