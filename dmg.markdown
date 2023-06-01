---
layout: page
title: Design Museum Gent
parent: Linked Data Event Stream
nav_order: 1
---


# **Design Museum Gent** 

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## General introduction
Design Museum Gent is the Design Museum in Ghent with a collection spanning from the fifteenth century to the present. Through collection presentations and temporary exhibitions, the museum wants to raise awareness about the impact of design on our daily lives. While the museum is currently closed during the building of a new wing "Ding" https://www.designmuseumgent.be/en/ding, Design Museum Gent keeps on sharing design through extra muros projects and the Collections of Ghent project.

## Published Metadata

| CIDOC                                                                                          | OSLO                          | CEST                                                                                                                                                 |
|------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| [publishing institution](http://www.cidoc-crm.org/html/5.0.4/cidoc-crm.html#P50)               | MaterieelDing.Beheerder       | [Naam Bewaarinstelling](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_bewaarinstelling)                                    |
| objectnumber                                                                                   | Object.identificator          | [Waarde Objectnummer](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Waarde_objectnummer)                                        |
| [objectname](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P41)                              | Entiteit.classificatie        | [Term Objectnaam](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Term_objectnaam)                                                |
| [title](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P102)                                  | MensgemaaktObject.titel       | [Titel](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Titel)                                                                    |
| [note](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P3)                                     | Entiteit.beschrijving         | [Korte Beschrijving](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Korte_beschrijving)                                          |
| [creator](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                                 | Activiteit.uitgevoerdDoor     | [Naam Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_vervaardiger)                                            |
| [creator activity](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P14)                        | Rol.activiteit of Rol.rol     | [Rol Vervaardiger](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Rol_vervaardiger)                                              |
| [place of creation](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P7)                        | Gebeurtenis.plaats            | [Naam plaats vervaardiging](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Naam_plaats_vervaardiging)                            |
| [time of creation - start](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P4)                 | Gebeurtenis.tijd              | [Begindatum](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Begindatum)                                                          |
| [time of creation - start - precision](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P4)     | Gebeurtenis.tijd              | [Precisie begindatum](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Precisie_begindatum)                                        |
| [time of creation - end](https://cidoc-crm.org/html/5.0.4/cidoc-crm.html#P4)                   | Gebeurtenis.tijd              | [Einddatum](https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/Einddatum)   

+ deelcollectie + materiaal + dimensie + materieelding.bestaatuit (onderdelen) + methode, plaats en datum van verwerving

The full mapping of the available metadata in this event stream can be found [here](https://app.gitbook.com/o/-MaDy7qNCF9HTgoNJPP6/s/-MaDyFunOfBA0nHUQZv_/datamappings/overzicht-velden-datamapping).

## Published Collections

 This Event Stream currently contains **3367 records** (2022-09-27) from the collection of **Design Museum Gent**. 
They are divided among the following **collections** (MensgemaaktObject.maaktDeelUitVan):
- Furniture ("meubels"): Middle Ages to Art Nouveau
- Model fragments ("modelfragmenten"): panels and ornaments of wooden furniture that were used to display and teach good craftsmanship
- Household electronics ("huishoudelijke apparaten"): mostly from the Belgian producer Nova
- Objects from the 1960s and 1970s ("jaren 1960" & "jaren 1970"): furniture, tableware, artworks, textiles, ... made in the 60s and 70s
- Italian postmodernism ("Italiaans postmodernisme"): many objects designed in the 1980s for Alessi, Memphis, ...
- Objects from particular designers ("Bořek Šípek", "Axel Enthoven", "Maarten Van Severen", "Piet Stockmans")

Art Nouveau and Art Deco objects are also published (with images) but these are not part of a named collection. They can be identified through the object number: objects starting with FH (Fonds Havermans) and most of the objects acquired in 1987 (object number starts with 1987-.

Design Museum Gent uses a different naming for partial and overarching records (for example a set of tableware containing multiple plates, forks, etc. or chairs and a table belonging to the same set). Overarching records have names that end in "-0_XX (amount of partial records)", while partial records end in "-1_XX", "-2_XX", ... depending on the amount of objects in a set. Only the overarching records have images that are publicly available and IIIF-manifests.

## LDES

link: [https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten](https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten)
