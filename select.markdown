---
layout: page
title: basic queries
parent: SparQL Endpoint
nav_order: 3
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## select

## count

## filter

## order

## bind


## union

*for example*

```
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX la: <https://linked.art/ns/terms/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
SELECT DISTINCT ?instelling ?title 
WHERE {
  ?object cidoc:P50_has_current_keeper ?instelling .
  ?object cidoc:P102_has_title ?title .
  ?object cidoc:P41i_was_classified_by ?identifier .
  ?identifier cidoc:P42_assigned ?objectnaam .
  ?objectnaam skos:prefLabel ?ojn .
  ?object cidoc:P108i_was_produced_by ?vervaardiging .
  ?vervaardiging cidoc:P14_carried_out_by ?maker .
  {?maker la:equivalent <https://stad.gent/id/agent/670003618> } UNION {?maker la:equivalent <https://stad.gent/id/agent/570025558>} .
} LIMIT 100!
```

## pagination

the SparQL endpoint limits results to 1.000 lines. If a query has more than 1.000 results, multiple queries, using OFFSET and LIMIT, are necessary to obtain the entire result. 

*for example*

```  
PREFIX purl: <http://purl.org/dc/terms/>
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

   SELECT DISTINCT ?priref ?label
   WHERE {
     SELECT ?versie ?priref ?label FROM <http://stad.gent/ldes/hva>
     WHERE { 
     
       ?versie purl:isVersionOf ?priref.
       ?versie cidoc:P128_carries ?draagt.
       ?draagt cidoc:P129_is_about ?over.
       ?over cidoc:P2_has_type ?type.
       ?type skos:prefLabel ?label.

       FILTER (regex(?label, "^circus$", "i"))

     } ORDER BY DESC(?versie)
  }
LIMIT 1000
OFFSET 1000!
```
