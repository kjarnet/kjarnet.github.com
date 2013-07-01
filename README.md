kjarnet.no
==========

My personal blog made with [jekyll bootstrap](http://jekyllbootstrap.com).

Mostly contains technical notes that may or may not be of use to others.

Server
------
To run local server: `gem install jekyll redcarpet` and then `jekyll server -w`.

Write posts and pages
---------------------

To create a post: `rake post title="Hello world"`.

To create a page: `rake page name="about.md"`
or `rake page name="pages/about.md"`.

Themes
------

Install:
`rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"`

Switch:
`rake theme:switch name="the-program"`

