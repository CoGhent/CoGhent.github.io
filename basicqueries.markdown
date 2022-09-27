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
  ?object cidoc:P102_has_title ?title.
} 
```

To get the results from only one heritage institution, specify which linked data eventstream you want to query using FROM.

*for example*

*This query will return the first distinct 1.000 titles of objects that are published in the linked data event stream from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT DISTINCT ?title FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
}
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20DISTINCT%20%3Ftitle%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%7D%20&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

When querying for fields that are linked to thesaurus terms or persons and institutions from the agents list, the result will be a external link to the concept.

*for example*

*This query will return the first 1.000 links to DISTINCT objectnames that are published in the event stream from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?objectname FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectname.
} 
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20DISTINCT%20%3Ftitle%20FROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%7D&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

To obtain the label of the terms, use SKOS or RDFS. 

*for example*

*This query will return the first 1.000 DISTINCT labels of objectnames that are published in the event stream by CoGhent.*


```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT DISTINCT ?label 
WHERE { 
  ?object cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectname.
  ?objectname skos:prefLabel ?label
}
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0APREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0A%0ASELECT%20DISTINCT%20%3Flabel%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP41i_was_classified_by%20%3Fidentifier.%0A%20%20%3Fidentifier%20cidoc%3AP42_assigned%20%3Fobjectname.%0A%20%20%3Fobjectname%20skos%3AprefLabel%20%3Flabel%0A%7D%0A&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

In addition, it is also possible to query on specific terms or agents, using the link to the external thesauri

*for example*

*This query will return the collecting cards that are published in the event streams.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?record ?title
WHERE { 
  ?object cidoc:P102_has_title ?title.
  ?object cidoc:P41i_was_classified_by ?identifier.
  ## look up with concept from AAT describing playing cards
  ?identifier cidoc:P42_assigned <http://vocab.getty.edu/aat/300192646>.
}
```
[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%20%20%3Fobject%20cidoc%3AP41i_was_classified_by%20%3Fidentifier.%0A%20%20%23%23%20look%20up%20by%20concept%20in%20AAT.%0A%20%20%3Fidentifier%20cidoc%3AP42_assigned%20%3Chttp%3A%2F%2Fvocab.getty.edu%2Faat%2F300192646%3E.%0A%7D%0A&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

## Count

## Filter

Use FILTER to further specify your result.

*for example*

*This query will return objects with titles that have the word 'Gent' in them that are published in the event stream from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title 
FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
  FILTER (regex(?title, "Gent", "i"))
} 
```

## Bind

## Distinct & Order by

Because of the specifications of a linked data event stream, multiple versions of records can be present. When metadata changes, the linked data event stream will publish a new version of a record, but an older version of the record still remains. To obtain solely the latest version of records, use ORDER BY to order the records chronologically (most recent versions first) and DISTINCT (to drop the following versions).

*for example*

*this query returns the first 1.000 records of the event stream of het Huis van Alijn. It orders the records on publishing date. Second, it keeps only the first priref and drops any possible older versions.*

```
PREFIX purl: <http://purl.org/dc/terms/>

SELECT DISTINCT ?priref
WHERE {
SELECT ?object ?priref FROM <http://stad.gent/ldes/hva>
WHERE { 
?object purl:isVersionOf ?priref.
} ORDER BY DESC(?versie)
}
```

## Union

To query multiple endpoint, it suffices to add the extra endpoint to the query.

*for example*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title 
FROM <http://stad.gent/ldes/hva> 
FROM <http://stad.gent/ldes/dmg> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
} 
```

However, when the query gets to complicated, it is better to use UNION.

*for example*

*this query returns 100 records with creator 'Joseph Buyens' from both the event streams of Industriemuseum en Archief Gent.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX la: <https://linked.art/ns/terms/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?institution ?title ?label
WHERE {
  ?object cidoc:P50_has_current_keeper ?institution .
  ?object cidoc:P102_has_title ?title .
  ?object cidoc:P108i_was_produced_by ?production .
  ?production cidoc:P14_carried_out_by ?maker .
  {?maker la:equivalent <https://stad.gent/id/agent/670003618> } UNION {?maker la:equivalent <https://stad.gent/id/agent/570025558>} .
  ?maker la:equivalent ?creator.
  ?creator rdfs:label ?label.
} LIMIT 100
```

## Pagination

the SparQL endpoint limits results to 1.000 lines. If a query has more than 1.000 results, multiple queries *(each containing the next 1.000 results)*, using OFFSET and LIMIT, are necessary to obtain the entire result. You will need to count (see above) how many results your query gives first, to know how many pages to query.

*for example*

*This query gets skips the first 1.000 results to return the next 1.000 results. It returns the records with subject circus from the collection of het Huis van Alijn.*

```  
PREFIX purl: <http://purl.org/dc/terms/>
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

   SELECT DISTINCT ?priref ?label
   WHERE {
     SELECT ?object ?priref ?label FROM <http://stad.gent/ldes/hva>
     WHERE { 
     
       ?object purl:isVersionOf ?priref.
       ?object cidoc:P128_carries ?carries.
       ?carries cidoc:P129_is_about ?about.
       ?about cidoc:P2_has_type ?type.
       ?type skos:prefLabel ?label.

       FILTER (regex(?label, "^circus$", "i"))

     } ORDER BY DESC(?versie)
  }
LIMIT 1000
OFFSET 1000
```
