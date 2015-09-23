---
layout: page
title: "React.js"
description: "presentasjon for CapraCon"
---
{% include JB/setup %}


React.js
========

* (Re)flux
* Immutable.js

Hva React er/ ikke er
---------------------

* IKKE et MVC/MV\*-rammeverk (ala Angular eller Ember)
* En frontend template-renderer -
  tenk på det som V-en i MVC
  (passer fint som template-delen i Backbone).
* Opererer med data som rene javascript-objekter,
  har ingen begrep om "modell",
  ingen støtte for kommunikasjon med server (Ajax)
  og ingen automatisk data-binding
  (synkronisering mellom view og modell).
  For annet enn trivielle applikasjoner
  anbefales andre biblioteker til dette,
  f.eks. jQuery og (re)flux.

Hva React gjør
--------------

* React gjør én ting, og det er lynkjapp rendring.
  Hemmeligheten bak dette er den Virtuelle DOMen.
  React er egentlig ganske dum,
  ved at hver gang du endrer på staten til en komponent
  rendres _hele_ komponenten (med barn) på nytt (fra scratch).
  _Men_, det rendres da ikke til DOM,
  men først til en in-memory representasjon av DOM-en.
  Så finner React diffen mellom
  forrige Virtuelle DOM og den nye Virtuelle DOM-en,
  og oppdaterer den faktiske DOM-en
  på en smart og effektiv måte.
  Dette går ganske kjapt,
  men hvis du har en komplisert struktur
  med mange komponenter
  er det ikke sikkert det er _kjapt nok_,
  og da har heldigvis React noen smarte
  muligheter for optimalisering,
  som jeg også tenkte vi skulle innom hvis vi får tid.

Men først....
-------------

* Litt kode:

        var TodoApp = React.createClass({

            getInitialState: function () {
                return {
                    initialText: "Nothing here",
                    editing: null
                };
            },

            componentDidMount: function () {
                // Init stuff
            },

            render: function () {
                // ...
            }

        });

* I React bygger du opp applikasjonen din av komponenter/components
  som du kan kombinere og sette sammen til mer avanserte komponenter.
  I eksempelet er TodoApp en komponent som
  bygger på en samling TodoItem komponenter.
* Hver komponent holder data i
  props og
  state.
  State er komponentens interne tilstand
  og endres kun av komponenten selv.
  Props skal derimot _ikke_ endres av komponenten selv
  men endres gjerne ifm. at foreldre-komponenten rendres.
  Du kan egentlig tenke på en komponent
  som en funksjon av props - 
  du sender props inn,
  og får en rendret (, interaktiv) komponent ut.

* Koden:
  getInitialState() er en funksjon for å sette evt. initielle verdier på staten.
  render() er selvfølgelig metoden som skal rendre komponenten til (Virtual) DOM - 
  Denne kommer vi tilbake til.
  I tillegg har man tilgang på flere
  [Lifecycle hooks](https://facebook.github.io/react/docs/component-specs.html#lifecycle-methods)

Render og events
----------------

    render: function () {
        var todoItems = this.props.todos.map(
            function (todo) {
                return TodoItem({key: todo.id, todo: todo});
        });

        return d.div(
            {className: 'container'},
            todoItems,
            d.button({onClick: this.handleClick}, "Klikk meg")
        );
    }

* I render bruker du komponentens props,
  og evt. state,
  og bygger et (virtuelt) DOM-tre.
* Ofte bygger du her på andre komponenter
  for å lage en mer kompleks komponent.
* Interaktive komponenter får du
  ved å binde event-handlere til
  (virtuelle) DOM-elementer med en onXxx-attributt.
  Dette er det nok noen som kjenner igjen som et anti-pattern,
  men det er _ikke_ det samme som
  å bruke onClick-attributtet på et vanlig DOM element,
  for bak kulissene er det event delegation som brukes.
  Det kan diskuteres om det er riktig "separation of concerns",
  men React argumenterer med at ...?

Forms / bruker input
--------------------

* Uncontrolled
  * defaultValue
  * ref
  * Les input-ens value med `this.refs.helloTo.getDOMNode().value;`
  * Kun trivielle forms.
* Controlled
  * value
  * onChange
  * Komponentens interne state følger input-ens value.


JSX
---

* En liten digresjon her:
  React kommer med en precompiler(?) som lar deg bruke et
  html-liknende syntax sammen med javascript-koden.
  Dette kaller de JSX.
  Jeg kommer ikke til å bruke dette her
  fordi jeg synes det er en unødvendig kompleksitet (?)
  som gir liten gevinst.

* I JSX:

        function render() {
            var todoItems = todos.map(
                function (todo) {
                    return (
                        <TodoItem key={todo.id} todo={todo} />
                    );
                }
            );

            return (
                <div className="container">
                    {todoItems}
                </div>
            );
        }

* Kompilert til javascript:

        function render() {
            var todoItems = todos.map(
                function (todo) {
                    return TodoItem({key: todo.id, todo: todo});
            });

            return d.div(
                {className: 'container'},
                todoItems
            );
        }

Optimalisering
------------

* Som nevnt er react ganske dum
  ved oppdatering av state,
  og rendrer hele den Virtuelle DOMen på nytt,
  noe som kan bety veldig mange unødvendige
  render- og sammenlikningsoperasjoner.
  Heldigvis har React også et triks eller to i ermet
  for å optimalisere dette.
* shouldComponentUpdate(nextProps, nextState) = true
* [Pure components](https://facebook.github.io/react/docs/pure-render-mixin.html).
* Immutable.js / immutable state.
  Det er her jeg synes react begynner å bli interessant :)

Arkitektur
----------

* Som nevnt har React et veldig begrenset ansvarsområde,
  og gjør seg best sammen med andre biblioteker.
  F.eks. er det vanlig å bruke jQuery til ajax,
  og mange bruker Backbone til bl.a.
  struktur og kommunikasjon mellom komponenter.
  Men et annet,
  kanskje mer interessant,
  alternativ til Backbone
  er Flux.

Flux
----

* [Overview](https://facebook.github.io/flux/docs/overview.html)

Reflux
------

* [GitHub](https://github.com/reflux/refluxjs)



