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

    <script type="text/javascript" src=”/something/fjas.js"></script>
    <script type="text/javascript" src=”/something/merfjas.js"></script>
    <script type="text/javascript" src=”/something/fjas.js"></script>
    <script type="text/javascript" src=”/something/fjas.js"></script>
    <script type="text/javascript" src=”/something/fjas.js"></script>
    <script type="text/javascript" src=”/something/fjas.js"></script>

</section>
 
<section>

Optimalisering / Konkatenering
------------------------------

    <script type="text/javascript" src=”/something/fjas.js"></script>
    <script type="text/javascript" src=”/something/merfjas.js"></script>
    <script type="text/javascript" src=”/somethingelse/massefjas.js"></script>
    <script type="text/javascript" src=”/something/fjas2.js"></script>
    ...

### &darr; ###

    <script type="text/javascript" src=”/something/all-fjas.js"></script>

</section>

<section>

Require.js
----------

define()

    // in my/store.js
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

requirejs()

    // in my/main.js
    requirejs(['jquery', 'canvas', 'my/store'],
    function   ($,        canvas,   Store) {
        var theStore = new Store();
        theStore.init();
    });

markup

    // in storepage.html
    ...
    or
    <script data-main="js/app.js" src="js/require.js"></script>


</section>


<section>

Fordeler
--------

- (utsette lasting til du trenger det)
- definere avhengigheter i hver js-fil
- importere templates fra eksterne filer som strenger
- 'innebygd' optimalisering/konkatenering/minifisering (r.js) og ferdig maven plugin (enkel/ kan progge egen)
- ingen endringer i html-fila ved konkatenering (kun ett seed/main-script).

</section>


<section>

Alternativer
------------

- **Grails** resource plugin
- **Rails** asset pipeline/ sprockets
- **Java** jawr, webutilities, combiner

</section>

<section>

Spørsmål?
----------

Presentasjon laget med [reveal.js](http://lab.hakim.se/reveal-js/).

</section>

