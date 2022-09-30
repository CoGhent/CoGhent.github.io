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

## Prefixes

- cidoc: http://www.cidoc-crm.org/cidoc-crm/
- adms: <http://www.w3.org/ns/adms#>
- la: https://linked.art/ns/terms/
- skos: <http://www.w3.org/2004/02/skos/core#>
- rdfs: <http://www.w3.org/2000/01/rdf-schema#>
- purl: http://purl.org/dc/terms/
- owl: http://www.w3.org/2002/07/owl#
- prov: <http://www.w3.org/ns/prov#>

## Properties

### Object

| **HIERARCHY**      |                                            **CIDOC**                                           |                  **OSLO**                 |                                                                       **CEST**                                                                       | **SPARQL PROPERTY**                                                                                    |
|--------------------|:----------------------------------------------------------------------------------------------:|:-----------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------:|--------------------------------------------------------------------------------------------------------|
| **GENERAL**        |                                                                                                |                                           |                                                                                                                                                      |                                                                                                        |
|                    | [publishing institution](http://www.cidoc-crm.org/html/5.0.4/cidoc-crm.html#P50)               | MaterieelDing.Beheerder                   | [Naam Bewaarinstelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_bewaarinstelling)                                    | cidoc:P50_has_current_keeper                                                                           |
|                    | objectnumber                                                                                   | Object.identificator                      | [Waarde Objectnummer](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Waarde_objectnummer)                                        | adms:identifier skos:notation                                                                          |
|                    | [title](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P102)                                  | MensgemaaktObject.titel                   | [Titel](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Titel)                                                                    | cidoc:P102_has_title                                                                                   |
|                    | [note](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P3)                                     | Entiteit.beschrijving                     | [Korte Beschrijving](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Korte_beschrijving)                                          | cidoc:P3_has_note                                                                                      |
|                    | [image](https://cidoc-crm.org/Property/p129-is-about/version-6.0)                              | Entiteit.isHetOnderwerpVan                | /                                                                                                                                                    | cidoc:P129i_is_subject_of                                                                              |
|                    | [current location](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P55)                        | MensgemaaktObject.locatie                 | [Identificatie huidige standplaats](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Identificatie_huidige_standplaats)            | cidoc:P55_has_current_location skos:prefLabel                                                          |
| **IDENTIFICATION** |                                                                                                |                                           |                                                                                                                                                      | **cidoc:P41i_was_classified_by**                                                                       |
|                    | [objectcategory](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P41)                          | Entiteit.classificatie                    | [Term Objectcategorie](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_objectcategorie)                                      | cidoc:P41i_was_classified_by cidoc:P42_assigned skos:prefLabel                                         |
|                    | [objectname](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P41)                              | Entiteit.classificatie                    | [Term Objectnaam](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_objectnaam)                                                | cidoc:P41i_was_classified_by cidoc:P42_assigned         skos:prefLabel                                                                      |
| **CREATION**       |                                                                                                |                                           |                                                                                                                                                      | **cidoc:P108i_was_produced_by**                                                                        |
|                    | [creator](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                                 | Activiteit.uitgevoerdDoor                 | [Naam Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_vervaardiger)                                            | cidoc:P108i_was_produced_by         cidoc:P14_carried_out_by          la:equivalent             rdfs:label                          |
|                    | [creator activity](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                        | Rol.activiteit of Rol.rol                 | [Rol Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Rol_vervaardiger)                                              | *under construction*                                                                                   |
|                    | [place of creation](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P7)                        | Gebeurtenis.plaats                        | [Naam plaats vervaardiging](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_plaats_vervaardiging)                            | cidoc:P108i_was_produced_by         cidoc:P7_took_place_at          la:equivalent             rdfs:label                            |
|                    | [time of creation](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P4)                         | Gebeurtenis.tijd                          | /                                                                                                                                                    | cidoc:P108i_was_produced_by cidoc:P4_has_time-span                                                     |
|                    | [technique](https://cidoc-crm.org/html/cidoc_crm_v7.1.1.html#P32)                              | Activiteit.gebruikteTechniek              | [Techniek](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Element/Techniek)                                                           | cidoc:P108i_was_produced_by cidoc:P32_used_general_technique cidoc:P2_has_type skos:prefLabel          |
| **ICONOGRAPHY**    |                                                                                                |                                           |                                                                                                                                                      | **cidoc:P62_depicts**                                                                                  |
|                    | [iconography subject](https://www.cidoc-crm.org/Property/p62-depicts/version-6.2.1)            | Entiteit.beeldtUit                        | [Naam afgebeelde gebeurtenis](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_afgebeelde_gebeurtenis)                        | *under construction*                                                                                   |
|                    | [iconography person/institution](https://www.cidoc-crm.org/Property/p62-depicts/version-6.2.1) | Entiteit.beeldtUit                        | [Naam afgebeelde persoon/instelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_afgebeelde_persoon_of_instelling)       | *under construction*                                                                                   |
| **SUBJECTS**       |                                                                                                |                                           |                                                                                                                                                      | **cidoc:P128_carries**                                                                                 |
|                    | [associated person/institution](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P67)           | InformatieObject.verwijstNaar             | [Naam geassocieerde persoon/instelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_geassocieerde_persoon_of_instelling) | cidoc:P128_carries cidoc:P67_refers_to cidoc:P2_has_type skos:prefLabel                                |
|                    | [associated subject](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P129)                     | InformatieObject.gaatOver                 | [Naam geassocieerd concept](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_geassocieerd_concept)                            | cidoc:P129_is_about cidoc:P67_refers_to cidoc:P2_has_type skos:prefLabel                               |
|                    | [associated period](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P67)                       | InformatieObject.verwijstNaar             | Naam geassocieerde periode                                                                                                                           | cidoc:P128_carries cidoc:P67_refers_to cidoc:P2_has_type skos:prefLabel                                |
| **ACQUISITION**    |                                                                                                | MaterieelDing.isOvergedragenBijVerwerving |                                                                                                                                                      | **cidoc:P24i_changed_ownership_through**                                                                 |
|                    | [acquisition technique](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P32)                   | Activiteit.gebruikteTechniek              | [Term verwervingsmethode](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_verwervingsmethode)                                | cidoc:P24i_changed_ownership_through cidoc:P32_used_general_technique cidoc:P2_has_type skos:prefLabel |
|                    | [acquisition location](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P7)                     | Gebeurtenis.plaats                        | [Plaats verwervingsbron](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Plaats_verwervingsbron)                                  | cidoc:P24i_changed_ownership_through cidoc:P7_took_place_at cidoc:P2_has_type skos:prefLabel           |
| **MATERIAL**       |                                                                                                | MaterieelDing.bestaatUit                  |                                                                                                                                                      | **cidoc:P45_consists_of**                                                                              |
|                    | [material](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P45)                                | MensgemaaktObject.materiaal               | [Term materiaal](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_materiaal)                                                  | cidoc:P45_consists_of cidoc:P2_has_type skos:prefLabel                                                 |

### Thesaurus

| **TERM**        | **OSLO**             | **SPARQL PROPERTY**           |
|-----------------|----------------------|-------------------------------|
| term            | skos:prefLabel       | skos:prefLabel                |
| priref          | Object.identificator | adms:identifier skos:notation |
| source          | owl:sameAs           | owl:sameAs                    |
| publishing date | prov:generetedAtTime | prov:generatedAtTime          |
