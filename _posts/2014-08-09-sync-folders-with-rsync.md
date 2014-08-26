---
layout: post
title: "Sync folders with rsync"
description: ""
category: how-tos
tags: [rsync]
---
{% include JB/setup %}

Rsync is a unix-tool to syncronize folders by only transferring the differing data to save bandwidth.

Here are two scripts I use for one-way syncing of my photos
to back them up to a usb thumb-drive.

Sync _from_ PC to usb:

    # Options:
    # -r copy directories recursively
    # -l copy symlinks as symlinks
    # -t preserve modification times
    # -b make backups (see --backup-dir)
    # -hh human readable with units in powers of 1024
    # -i list a list of changes to each file
    # --size-only skip files with no change in size
    # --delete delete files from the receiving side that aren't on the sending side
    # --exclude= exclude files matching the pattern. Repeat option for multiple patterns.
    rsync -rltbhhi --backup-dir=./Fotoalbum_backup --log-file=./sync_fra_pc_log.txt --exclude='*.ini' --exclude='*.db' --exclude='.*' --delete --progress --size-only ~/Pictures/Fotoalbum ./ 

Sync _to_ PC from usb:

   # Options:
   # -r copy directories recursively
   # -l copy symlinks as symlinks
   # -t preserve modification times
   # -b make backups (see --backup-dir)
   # -hh human readable with units in powers of 1024
   # -i list a list of changes to each file
   # --size-only skip files with no change in size
   # --delete delete files from the receiving side that aren't on the sending side
   # --exclude= exclude files matching the pattern. Repeat option for multiple patterns.
   rsync -rltbhhi --backup-dir=Fotoalbum_backup --log-file=./sync_til_pc_log.txt --exclude='*.ini' --exclude='*.db' --exclude='.*' --delete --progress --size-only ./Fotoalbum ~/Pictures/ 


They are run from the usb drive as shell-scripts.

