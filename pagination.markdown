---
layout: page
title: union and pagination
parent: SparQL Endpoint
nav_order: 4
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## union

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
