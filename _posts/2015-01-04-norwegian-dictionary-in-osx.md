---
layout: post
title: "Norwegian dictionary in OSX"
description: ""
category: how-tos
tags: [osx, norwegian]
---
{% include JB/setup %}

OSX (Yosemite) doesn't ship with a Norwegian spellchecker (for Pages etc.), so you have to add this yourself.

OS X's spellchecker is based on Hunspell meaning you can (in theory haven't tested this) use any of their dictionaries (which also drive the spellchecking in LibreOffice, Firefox, Chrome and many others).

A large collections can be found on OpenOffice's servers: http://archive.services.openoffice.org/pub/mirror/OpenOffice.org/contrib/dictionaries/

If I read the info file correctly, nb_NO.zip should contain both Nynorsk and Bokmål. Just put them in ~/Library/Spelling, log out and in again and you should be able to select them.

Source:
_ _ _

* [http://www.reddit.com/r/osx/comments/1zyv1z/i_need_a_norwegian_language_pack/cfy9eml](http://www.reddit.com/r/osx/comments/1zyv1z/i_need_a_norwegian_language_pack/cfy9eml)

