---
layout: page
title: "Adminweb"
description: ""
---
{% include JB/setup %}

- Spring boot
    - Autoconfig
    - Annotations
    - Component Scan
    - Ingen xml!

- Struktur applikasjoner/adminweb/
    - src/main/java/ :
        - AdminWebStarter : main-metode for embedded Tomcat
        - AdminWebConfig : config...
        - rest/ : Jersey rest tjenester for data til frontend
        - rest/typer/ : adapter-klasser fra domene-klasser til JSON tilpasset frontend
    - src/main/resources/ :
        - templates/ : Velocity templates
        - static/ : Statiske ressurser som JavaScript og CSS/LESS
        - config/ : application[-development].properties -Dspring.profiles.active=development

- Datalag: 
    - komponenter/registerdata/ : JpaRepository (interfaces) - automgisk implementasjon - spring-data - bruker:
    - komponenter/domene/ : Gamle (og nye) Hibernate domene-klasser/ Entity. (Problem med GenDAO)

- TekstmalPreview
    - Lisa server
    - komponenter/cxf/ (Apache CXF JAX-RS implementasjon)
    - Brukes av tekstmal-sidene via Ajax m/CORS (Cross Origin Resource Sharing)
    - Adressen til lisa-server må derfor konfigureres i application.properties



