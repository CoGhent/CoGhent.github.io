---
layout: page
title: Prefixes & Properties
parent: SparQL Endpoint
nav_order: 2
---

# Prefixes & Properties

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## General

Compose your query by using below prefixes and properties. 

*for example - This query selects all titles in the event streams of CoGhent*
```
SELECT ?title
WHERE { 
  ?object <http://www.cidoc-crm.org/cidoc-crm/P102_has_title> ?title.
} 
```

To make the query more readable when querying multiple fields, we split the URL. The portion that always remains the same is the PREFIX, the unique value that follows is the property.

*for example - Previous query becomes:*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title
WHERE { 
  ?object cidoc:P102_has_title ?title.
} 
```
Sometimes multiple properties need to be used to get to the value needed.

*for example*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?objectname 
WHERE { 
  ?object cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectname.
} 
```

To help build your queries, the cogent querybuilder can be used: [https://coghentapps.herokuapp.com/querybuilder](https://coghentapps.herokuapp.com/querybuilder)

## Prefixes

PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/<span>><br>
PREFIX adms: <<span>http://www.w3.org/ns/adms#<span>><br>
PREFIX dataeu: <<span>http://data.europa.eu/m8g/<span>><br>
PREFIX la: <<span>https://linked.art/ns/terms/<span>><br>
PREFIX skos: <<span>http://www.w3.org/2004/02/skos/core#<span>><br>
PREFIX rdfs: <<span>http://www.w3.org/2000/01/rdf-schema#<span>><br>
PREFIX purl: <<span>http://purl.org/dc/terms/<span>><br>
PREFIX owl: <<span>http://www.w3.org/2002/07/owl#<span>><br>
PREFIX prov: <<span>http://www.w3.org/ns/prov#<span>><br>

## Properties

### Object

|                                            **CIDOC**                                           |                  **OSLO**                 |                                                                       **CEST**                                                                       | **SPARQL PROPERTY**                                                                                    |
|:----------------------------------------------------------------------------------------------:|:-----------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------:|--------------------------------------------------------------------------------------------------------|
|**GENERAL**                                                                                                |                                           |                                                                                                                                                      |                                                                                                        |
| [publishing institution](http://www.cidoc-crm.org/html/5.0.4/cidoc-crm.html#P50)               | MaterieelDing.Beheerder                   | [Naam Bewaarinstelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_bewaarinstelling)                                    | cidoc:P50_has_current_keeper                                                                           |
| objectnumber                                                                                   | Object.identificator                      | [Waarde Objectnummer](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Waarde_objectnummer)                                        | adms:identifier<br> skos:notation                                                                          |
| [title](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P102)                                  | MensgemaaktObject.titel                   | [Titel](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Titel)                                                                    | cidoc:P102_has_title                                                                                   |
| [note](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P3)                                     | Entiteit.beschrijving                     | [Korte Beschrijving](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Korte_beschrijving)                                          | cidoc:P3_has_note                                                                                      |
| [image](https://cidoc-crm.org/Property/p129-is-about/version-6.0)                              | Entiteit.isHetOnderwerpVan                | /                                                                                                                                                    | cidoc:P129i_is_subject_of                                                                              |
| [current location](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P55)                        | MensgemaaktObject.locatie                 | [Identificatie huidige standplaats](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Identificatie_huidige_standplaats)            | cidoc:P55_has_current_location<br> skos:prefLabel                                                          |
|**IDENTIFICATION**                                                                                                |                                           |                                                                                                                                                      | **cidoc:P41i_was_classified_by**                                                                       |
| [objectcategory](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P41)                          | Entiteit.classificatie                    | [Term Objectcategorie](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_objectcategorie)                                      | cidoc:P41i_was_classified_by<br> cidoc:P42_assigned<br> skos:prefLabel                                         |
| [objectname](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P41)                              | Entiteit.classificatie                    | [Term Objectnaam](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_objectnaam)                                                | cidoc:P41i_was_classified_by<br> cidoc:P42_assigned<br>         skos:prefLabel                                                                      |
|**PRODUCTION**                                                                                                |                                           |                                                                                                                                                      | **cidoc:P108i_was_produced_by**                                                                        |
| [creator](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                                 | Activiteit.uitgevoerdDoor                 | [Naam Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_vervaardiger)                                            | cidoc:P108i_was_produced_by<br>         cidoc:P14_carried_out_by<br>          la:equivalent<br>             rdfs:label                          |
| [creator activity](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                        | Rol.activiteit of Rol.rol                 | [Rol Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Rol_vervaardiger)                                              | *under construction*                                                                                   |
| [place of creation](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P7)                        | Gebeurtenis.plaats                        | [Naam plaats vervaardiging](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_plaats_vervaardiging)                            | cidoc:P108i_was_produced_by<br>         cidoc:P7_took_place_at<br>          la:equivalent<br>             rdfs:label                            |
| [time of creation](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P4)                         | Gebeurtenis.tijd                          | /                                                                                                                                                    | cidoc:P108i_was_produced_by<br> cidoc:P4_has_time-span                                                     |
| [technique](https://cidoc-crm.org/html/cidoc_crm_v7.1.1.html#P32)                              | Activiteit.gebruikteTechniek              | [Techniek](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Element/Techniek)                                                           | cidoc:P108i_was_produced_by<br> cidoc:P32_used_general_technique<br> cidoc:P2_has_type<br> skos:prefLabel          |
|**ICONOGRAPHY**                                                                                                |                                           |                                                                                                                                                      | **cidoc:P62_depicts**                                                                                  |
| [iconography subject](https://www.cidoc-crm.org/Property/p62-depicts/version-6.2.1)            | Entiteit.beeldtUit                        | [Naam afgebeelde gebeurtenis](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_afgebeelde_gebeurtenis)                        | *under construction*                                                                                   |
| [iconography person/institution](https://www.cidoc-crm.org/Property/p62-depicts/version-6.2.1) | Entiteit.beeldtUit                        | [Naam afgebeelde persoon/instelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_afgebeelde_persoon_of_instelling)       | *under construction*                                                                                   |
|**ASSOCIATIONS**                                                                                                |                                           |                                                                                                                                                      | **cidoc:P128_carries**                                                                                 |
| [associated person/institution](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P67)           | InformatieObject.verwijstNaar             | [Naam geassocieerde persoon/instelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_geassocieerde_persoon_of_instelling) | cidoc:P128_carries<br> cidoc:P67_refers_to<br> cidoc:P2_has_type<br> rdfs:label                                |
| [associated subject](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P129)                     | InformatieObject.gaatOver                 | [Naam geassocieerd concept](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_geassocieerd_concept)                            | cidoc:P128_carries<br> cidoc:P129_is_about<br> cidoc:P2_has_type<br> skos:prefLabel                               |
| [associated period](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P67)                       | InformatieObject.verwijstNaar             | Naam geassocieerde periode                                                                                                                           | cidoc:P128_carries<br> cidoc:P67_refers_to<br> cidoc:P2_has_type<br> skos:prefLabel                                |
|**ACQUISITION**                                                                                                | MaterieelDing. isOvergedragenBijVerwerving |                                                                                                                                                      | **cidoc:P24i_changed_ownership_through**                                                                 |
| [acquisition technique](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P32)                   | Activiteit.gebruikteTechniek              | [Term verwervingsmethode](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_verwervingsmethode)                                | cidoc:P24i_changed_ownership_through<br> cidoc:P32_used_general_technique<br> cidoc:P2_has_type<br> skos:prefLabel |
| [acquisition location](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P7)                     | Gebeurtenis.plaats                        | [Plaats verwervingsbron](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Plaats_verwervingsbron)                                  | cidoc:P24i_changed_ownership_through<br> cidoc:P7_took_place_at<br> cidoc:P2_has_type<br> skos:prefLabel           |
| acquisition date                   | Gebeurtenis.tijd - Periode begin              | [Waarde verwervingsdatum](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Waarde_verwervingsdatum)                                | cidoc:P24i_changed_ownership_through<br> cidoc:P4_has_time-span<br> dataeu:startTime |
| acquisition date                      | Gebeurtenis.tijd - Periode eind                        | [Waarde verwervingsdatum](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Waarde_verwervingsdatum)                                     | cidoc:P24i_changed_ownership_through<br> cidoc:P4_has_time-span<br> dataeu:endTime           |
|**MATERIAL**                                                                                                | MaterieelDing.bestaatUit                  |                                                                                                                                                      | **cidoc:P45_consists_of**                                                                              |
| [material](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P45)                                | MensgemaaktObject.materiaal               | [Term materiaal](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_materiaal)                                                  | cidoc:P45_consists_of<br> cidoc:P2_has_type<br> skos:prefLabel                                                 |

### Thesaurus

| **TERM**        | **OSLO**             | **SPARQL PROPERTY**           |
|-----------------|----------------------|-------------------------------|
| term            | skos:prefLabel       | skos:prefLabel                |
| priref          | Object.identificator | adms:identifier skos:notation |
| source          | owl:sameAs           | owl:sameAs                    |
| publishing date | prov:generetedAtTime | prov:generatedAtTime          |


