---
layout: presentation
title: JavaScript i bygget
description: Presentasjon om inkludering av JavaScript i Java web-applikasjoner.
---

<section>

Javascript i bygget
===================
![JavaScript Sabotage](/assets/sabotage_js_small.png)

<small>

(Themes:
[default](?theme=default)
[beige](?theme=beige)
[moon](?theme=moon)
[night](?theme=night)
[serif](?theme=serif)
[simple](?theme=simple)
[sky](?theme=sky)
[solarized](?theme=solarized)
)

</small>

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

<aside class="notes">

- modulær javascript
- mange filer og avhengigheter
- inkludere på en/ flere websider
- én script tag pr fil
- må redigere webisda
- importere avhengigheter i riktig rekkefølge

</aside>

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

<aside class="notes">

- flette sammen
- én request
- før deploy til prod
- separate ved utvikling (debugging)
- før bygg til prod
- erstatte alle script-linjer med én
- manuelt
- duplisert liste i js-bygg-fil

</aside>

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

<aside class="notes">

- eksempel fra KF
- AMD: require.js
- define() og requirejs()
- define:
  - definere moduler
  - avhengigheter

</aside>
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


<aside class="notes">

- requirejs() = java main()
- trigger import-kjeden
- eneste import
- require.js laster inn resten

</aside>
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

<aside class="notes">

- Java-liknende dependency management
  - moduler og avhengigheter i samme fil
  - ikke passe på rekkefølge
- importere kun main-fil
  - ikke endre html ved optimalisering
- maven plugin
- bonus: plugin for templates
  - selvstendige, testbare views
- ulemper: 
  - ekstra bibliotek
  - konfig for optimalt med andre lib.

</aside>
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

<aside class="notes">

- require.js: reint javascript lib
- serverside rammeverk:
  - Rails asset pipeline
    - avhengigheter i kommentarer
    - støtter optimalisering, coffeescript, etc.
  - Grails resource plugin
    - avhengigheter i Resources.groovy
  - java
    - ingen dep. man. for Spring MVC, Wicket, Play eller Lift
    - generelle lib: jawr, webutilities, combiner

</aside>
</section>

<section>

Spørsmål?
----------

![Confused Lolcat](/assets/lolcat_confused.jpg)


<small>
*(Foiler finnes på [kjarnet.no/jsibyggetpres](http://kjarnet.no/jsibyggetpres?theme=serif).*   
*Laget med [reveal.js](http://lab.hakim.se/reveal-js/)
og [markdown](http://daringfireball.net/projects/markdown/).)*
</small>

<aside class="notes">

- Hvor mange her har brukt noe dependency management for JavaScript?
- Hva har du brukt? 
- Var du fornøyd?
- Hvor mange har klart seg fint uten noe js-avhengighetssystem?

</aside>
</section>

