---
layout: presentation
title: JavaScript i bygget
description: Presentasjon om inkludering av JavaScript i Java web-applikasjoner.
---

<section>

Javascript i bygget
===================
![JavaScript Sabotage](/assets/sabotage_js_small.png)

</section>

<section>

Problemet
---------

    <html>
        <script type=".." src="/js/jquery.js"></script>
        <script type=".." src="/js/underscore.js"></script>
        <script type=".." src="/js/backbone.js"></script>
        <script type=".." src="/js/my/cart.js"></script>
        <script type=".." src="/js/my/inventory.js"></script>
        <script type=".." src="/js/my/store.js"></script>
        ..


</section>
 
<section>

Optimalisering
--------------

    <script type="..." src="/js/backbone.js"></script>
    <script type="..." src="/js/my/cart.js"></script>
    <script type="..." src="/js/my/inventory.js"></script>
    <script type="..." src="/js/my/store.js"></script>
    ...

&darr;   
Federate + Minify   
&darr;

    <script type... src="/js/my.min.js"></script>

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
    <script src="js/require.js"></script>
    <script src="js/main.js"></script>

... eller ...

    <script src="js/require.js" data-main="js/main.js"></script>


</section>


<section>

Fordeler
--------

- Definer avhengigheter sammen med modulen
- Ingen endringer i markupen ved optimalisering
- Maven plugin for optimalisering
- Importere templates fra eksterne filer

&nbsp;

### Ulemper

- Et ekstra bibliotek
- Krever litt konfigurering

</section>


<section>

Alternativer
------------

- **Rails**: asset pipeline/ sprockets
- **Grails**: resource plugin
- **Java**:
[jawr](https://jawr.java.net/), 
[webutilities](https://code.google.com/p/webutilities/), 
[combiner](https://github.com/nzakas/combiner)

</section>

<section>

Spørsmål?
----------

![Confused Lolcat](/assets/lolcat_confused.jpg)


<small>*(Presentasjon laget med [reveal.js](http://lab.hakim.se/reveal-js/)
og [markdown](http://daringfireball.net/projects/markdown/).)*</small>

</section>

