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
                var todoItems = this.props.todos.map(
                    function (todo) {
                        return TodoItem({key: todo.id, todo: todo});
                });

                return d.div(
                    {className: 'container'},
                    todoItems
                );
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
* getInitialState() er en funksjon for å sette evt. initielle verdier på staten.
  render() er selvfølgelig metoden som skal rendre komponenten til (Virtual) DOM.
  I tillegg har man tilgang på flere Lifecycle hooks

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
* shouldComponentUpdate?
* Pure components.
* Immutable.js / immutable state.
  Det er her jeg synes react begynner å bli interessant :)
