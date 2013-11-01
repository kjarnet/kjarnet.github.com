---
layout: post
title: "Chromium Beta"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Install Latest Beta of Chromium in Ubuntu 13.10
===============================================

1. Add [Arcot's ppa](https://launchpad.net/~saiarcot895/+archive/chromium-beta): `sudo add-apt-repository ppa:saiarcot895/chromium-beta`
2. Get api-keys and oauth details: http://www.chromium.org/developers/how-tos/api-keys (use old console mode)
3. Add export-lines in .bash_profile or similar (and save in supersecret place).

        export GOOGLE_API_KEY="api_key"
        export GOOGLE_DEFAULT_CLIENT_ID="client_id"
        export GOOGLE_DEFAULT_CLIENT_SECRET="client_secret"

4. Apt update and upgrade
5. Start chromium-browser from terminal (or research how to add env variables to .desktop scripts).



