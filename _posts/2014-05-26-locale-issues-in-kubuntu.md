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

## Locale explenation ##

* LC\_NUMERIC: Numeric formatting.
* LC\_PAPER: Default paper size (A4, Letter etc.).
* LC\_TIME: Date and time formats.
* LC\_ALL: Setting this overrides all other LC\_\* and is not recommended.
* LANG: Default locale.
* LANGUAGE: A colon-separated list of _languages_  (not locales) preferred used in applications. E.g. `nb:se:en`.


## Locale in KDE ##
KDE offers a gui in system settings for changing locale.
However, there is
[a bug (at least in Kubuntu)](https://bugs.launchpad.net/ubuntu/+source/kde-runtime/+bug/1322968)
that makes this set invalid locale-settings
when trying to set language and country independently.
E.g. if I set country to Norway
(to get Norwegian regional settings
for currency, time etc.),
and langage to American English,
locale is set to the invalid value `en_NO.UTF-8`.
One proposed fix is
setting language to British English instead of American.
Another is manually editing 
`~/.kde/env/setlocale.sh`
which appearently is the file used by the settings-gui.

## No norwegian letters in Chromium ##

_Tested in Kubuntu 14.04_

This problem is accompanied with error-messages
when apt-get tries to update locale settings.
These messages reveal that it tries to set locale to "en\_NO.UTF-8"
which of course doesn't exist.
See solution above.

