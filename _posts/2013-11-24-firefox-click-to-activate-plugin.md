---
layout: post
title: "Firefox click to activate plugin"
description: ""
category: 
tags: [firefox]
---
{% include JB/setup %}

Click to Activate Plugin in Firefox
===================================

This describes how to enable a feature like Chrome's
"click to activate plugin" in Firefox.

 - In about:config "plugins.click\_to\_play" must be "true".
 - On about:addons (plugins page) required plugin must be "Ask to activate"
 - That's it :)

Alternatively, also install plugin to enable per-element (instead of per-page /-domain) control:
[Click to Play per-element](https://addons.mozilla.org/en-US/firefox/addon/click-to-play-per-element/) 
(which this howto is taken from).

Also: "if you want to enable the plugin on the page and not the whole website by clicking the "Allow Now" button from urlbar plugin icon (like in Firefox 23 "Activate" button)
in about:config "plugin.sessionPermissionNow.intervalInMinutes" set it to 0".

