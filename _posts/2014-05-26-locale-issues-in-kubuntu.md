---
layout: post
title: "Locale Issues in (K)ubuntu"
description: ""
category: how-tos
tags: [ubuntu, locale]
---
{% include JB/setup %}

I've had some issues with the Locale-settings in ubuntu,
mostly related to displaying/ writing norwegian letters (like æøå).

## No norwegian letters in Chromium ##

_Tested in Kubuntu 14.04_

This problem is accompanied with error-messages
when apt-get tries to update locale settings.
These messages reveal that it tries to set locale to "en\_NO.UTF-8"
which of course doesn't exist.
I never found out where this came from,
but the solution seems to be to add a missing line in
`/etc/default/locales`:

    LC_ALL="en_US.UTF-8"

