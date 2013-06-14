---
layout: post
title: "Recover Apt"
description: "Recovering apt after an upgrade went to H***"
category: technotes
tags: [apt]
---
{% include JB/setup %}

Problem: 
ran `apt-get dist-upgrade` and pc crashed in the middle of the process of upgrading the kernel.
After a forced reboot apt-get update says I must manually `dpkg --configure -a`,
but this doesn't work.
`apt-get -f install` is also suggested but this gives 
"unable to execute installed pre-removal script".

Solution turned out to be installing the kernel-package manually:
`sudo dpkg -i /var/cache/apt/archives/linux-image-3.8.0-25-generic_3.8.0-25.37_amd64.deb`

---
Sources:

* http://blog.kalleberg.org/post/746314210/recovering-from-a-broken-apt-get-upgrade

