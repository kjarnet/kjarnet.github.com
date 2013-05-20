---
layout: presentation
title: JavaScript i bygget
description: Presentasjon om inkludering av JavaScript i Java web-applikasjoner.
---

<section>

JavaScript i bygget
===================
bilde??

</section>

<section>

Problemet
---------

    <script type="..." src=”/js/jquery.js" />
    <script type="..." src=”/js/underscore.js" />
    <script type="..." src=”/js/backbone.js" />
    <script type="..." src=”/js/my/cart.js" />
    <script type="..." src=”/js/my/inventory.js" />
    <script type="..." src=”/js/my/store.js" />

</section>
 
<section>

Optimalisering / Konkatenering
------------------------------

    <script type="..." src=”/js/backbone.js" />
    <script type="..." src=”/js/my/cart.js" />
    <script type="..." src=”/js/my/inventory.js" />
    <script type="..." src=”/js/my/store.js" />
    ...

### &darr; ###

    <script type... src=”/js/my.min.js" />

</section>

<section>

Require.js - moduler
--------------------

define()

    // i js/my/store.js
    define(["my/cart", "my/inventory"],
        function(Cart, Inventory) {
            var Store = function(title) {
              this.title = title;
              this.inventory = new Inventory();
            };
            Store.prototype.getStock = function(){
              return this.inventory.getLength();
            };
            return Store;
        }
    );

</section>

<section>

Require.js - main-script
------------------------

requirejs()

    // i js/main.js
    requirejs(['jquery', 'canvas', 'my/store'],
    function   ($,        canvas,   Store) {
        var theStore = new Store();
        theStore.init();
    });

markup

    // i storepage.html
    <script src=”js/require.js" type... />
    <script src=”js/app.js" type... />
    // ... eller ...
    <script data-main="js/app.js" src="js/require.js" />


</section>


<section>

Fordeler
--------

- moduler som definerer sine egne avhengigheter
- ingen endringer i markupen ved konkatenering
- maven plugin for optimalisering
- importere templates fra eksterne filer

</section>


<section>

Alternativer
------------

- **Rails** asset pipeline/ sprockets
- **Grails** resource plugin
- **Java** jawr, webutilities, combiner

</section>

<section>

Spørsmål?
----------

![Confused Lolcat](/assets/lolcat_confused.jpg)


<small>*(Presentasjon laget med [reveal.js](http://lab.hakim.se/reveal-js/)
og [markdown](http://daringfireball.net/projects/markdown/).)*</small>

</section>

