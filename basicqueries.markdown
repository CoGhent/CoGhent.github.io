---
layout: page
title: Basic queries
parent: SparQL Endpoint
nav_order: 3
---

# Basic Queries

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Select

Use SELECT to define which data you want to have returned with your query. 

*for example*

*This query will return the first 1.000 titles of objects that are published in the linked data event streams from the five participating cultural heritage institutions.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title
WHERE { 
  ?record cidoc:P102_has_title ?title.
} 
```

To get the results from only one heritage institution, specify which linked data eventstream you want to query using FROM.

*for example*

*This query will return the first 1.000 titles of objects that are published in the linked data event streams from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?record cidoc:P102_has_title ?title.
}
```

When querying for fields that are linked to thesaurus terms or persons and institutions from the agents list, the result will be a external link to the concept.

*for example*
*This query will return the first 1.000 links to objectnames that are published in the linked data event streams from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?ojectnaam FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?record cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?ojectnaam.
} 
```

To obtain the label of the terms, use SKOS or RDFS. 

*for example*
*This query will return the first 1.000 labels of objectnames that are published in the linked data event streams from het Huis van Alijn.*


```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?label FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?record cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectnaam.
  ?objectnaam skos:prefLabel ?label
}
```

In addition, it is also possible to query on specific terms or agents, using the link to the external thesauri

*for example*
*This query will return the collecting cards that are published in the linked data event streams from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?record ?title FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?record cidoc:P102_has_title ?title.
  ?record cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned <http://vocab.getty.edu/aat/300192646>.
}
```

## Count

## Filter

Use FILTER to further specify your result.

*for example*
*This query will return all the titles that have the word 'Gent' in them that are published in the linked data event streams from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title 
FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?start cidoc:P102_has_title ?title.
  FILTER (regex(?title, "Gent", "i"))
} 
```

## Bind

## Distinct

## Order by

## Union

To query on multiple endpoint, it suffices to add the endpoints to the query.

*for example*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title 
FROM <http://stad.gent/ldes/hva> 
FROM <http://stad.gent/ldes/dmg> 
WHERE { 
  ?start cidoc:P102_has_title ?title.
} 
```

However, when the query gets to complicated, it is better to use UNION.

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
} LIMIT 100
```

## pagination

the SparQL endpoint limits results to 1.000 lines. If a query has more than 1.000 results, multiple queries *(each containing the next 1.000 results)*, using OFFSET and LIMIT, are necessary to obtain the entire result. 

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
OFFSET 1000
```
