---
layout: post
title: "Vim and word wrap"
description: ""
category: how-tos
tags: [vim]
---
{% include JB/setup %}

As I use vim mostly for programming,
I have disabled automatic word-wrap by default.
Follow these steps to enable automatic soft\* word-wrap
(without inserting hard\* linebreaks)
on a per-window basis.
(As can be useful when writing or reading long texts.)


Disable automatic hard\* linebreak: `:set textwidth=0`.
This can be put in vimrc (without ":")
to make this the default behaviour (which it actually already is).

Disable wrap based on terminal size: `:set wrapmargin=0`.
Should also be put in vimrc.

Enable wordwrap:

    :set wrap       " enable soft\* linebreak  
    :set linebreak  " only break at a character in the 'breakat' option  
    :set nolist     " list (marking whitepsace) might disable linebreak

If you haven't enabled automatic hard linebreak,
terminal-based wrap or list-mode,
`:set wrap` and `:set linebreak` should suffice.
And, even though
[the manual](http://vimdoc.sourceforge.net/htmldoc/options.html#%27linebreak%27)
says `linebreak` is "not used" when `wrap` is not set,
only `:set linebreak` seems to be required in most cases.


\*) "hard linebreak" means actual newline-characters
that are saved with the document,
while "soft linebreaks" are when the editor dynamically wraps the text
to fit the width of the window.

