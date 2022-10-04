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

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%7D%20%0A&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

To get the results from only one heritage institution, specify which linked data eventstream you want to query using FROM.

*for example*

*This query will return the first distinct 1.000 titles of objects that are published in the linked data event stream from het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
}
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%20FROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%7D&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

When querying for fields that are linked to thesaurus terms or persons and institutions from the agents list, the result will be a external link to the concept.

*for example*

*This query will return the first 1.000 links to objectnames that are published in the CoGhent event streams.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?objectname 
WHERE { 
  ?object cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectname.
} 
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Fobjectname%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP41i_was_classified_by%20%3Fidentifier.%0A%20%20%3Fidentifier%20cidoc%3AP42_assigned%20%3Fobjectname.%0A%7D%20&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

To obtain the label of the terms, use SKOS or RDFS. 

*for example*

*This query will return the first 1.000 labels of objectnames that are published in the CoGhent event streams.*


```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?label 
WHERE { 
  ?object cidoc:P41i_was_classified_by ?identifier.
  ?identifier cidoc:P42_assigned ?objectname.
  ?objectname skos:prefLabel ?label
}
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0APREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0A%0ASELECT%20%3Flabel%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP41i_was_classified_by%20%3Fidentifier.%0A%20%20%3Fidentifier%20cidoc%3AP42_assigned%20%3Fobjectname.%0A%20%20%3Fobjectname%20skos%3AprefLabel%20%3Flabel%0A%7D%0A&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

In addition, it is also possible to query on specific terms or agents, using the link to the external thesauri

*for example*

*This query will return the records with objectname collecting card that are published in the CoGhent event streams.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?object ?title
WHERE { 
  ?object cidoc:P102_has_title ?title.
  ?object cidoc:P41i_was_classified_by ?identifier.
  ## look up with concept from AAT describing playing cards
  ?identifier cidoc:P42_assigned <http://vocab.getty.edu/aat/300192646>.
}
```
[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%20%20%3Fobject%20cidoc%3AP41i_was_classified_by%20%3Fidentifier.%0A%20%20%23%23%20look%20up%20by%20concept%20in%20AAT.%0A%20%20%3Fidentifier%20cidoc%3AP42_assigned%20%3Chttp%3A%2F%2Fvocab.getty.edu%2Faat%2F300192646%3E.%0A%7D%0A&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

## Count

*for example*

*This query returns the number of titles that are published in the event stream of het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT COUNT( DISTINCT ?title) FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
}

```
[try live](https://stad.gent/sparql?default-graph-uri=&query=PREFIX+cidoc%3A+%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0D%0A%0D%0ASELECT+COUNT%28+DISTINCT+%3Ftitle%29+FROM+%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E+%0D%0AWHERE+%7B+%0D%0A++%3Fobject+cidoc%3AP102_has_title+%3Ftitle.%0D%0A%7D%0D%0A&format=text%2Fhtml&should-sponge=&timeout=0&signal_void=on)

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
[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%20%0AFROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%20%20FILTER%20(regex(%3Ftitle%2C%20%22Gent%22%2C%20%22i%22))%0A%7D%20&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

## Bind

To manipulate the data in your query, BIND can be used.

BIND & REPLACE

*for example*

*this query returns the first 100 records with 'Gent' in the title of the event stream of het Huis van Alijn and replaces Gent with Ghent.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?newtitle
FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
  FILTER (regex(?title, "Gent", "i"))
  BIND (REPLACE(str(?title), "Gent", "Ghent") AS ?newtitle).
} LIMIT 100
```

[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Fnewtitle%0AFROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%20%20FILTER%20(regex(%3Ftitle%2C%20%22Gent%22%2C%20%22i%22))%0A%20%20BIND(REPLACE(str(%3Ftitle)%2C%20%22Gent%22%2C%20%22Ghent%22)%20AS%20%3Fnewtitle).%0A%7D%20LIMIT%20100&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

BIND & CONCAT

*for example*

*this query returns the link to the (different versions) of the event stream of het Huis van Alijn for a certain objectnumber (in filter).*

```
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX adms: <http://www.w3.org/ns/adms#>
PREFIX prov: <http://www.w3.org/ns/prov#>
		
SELECT DISTINCT ?ldes FROM <http://stad.gent/ldes/hva> 
WHERE { 
  ?object adms:identifier ?identifier.
  ?identifier skos:notation ?objectnumber.
  FILTER (regex(?objectnumber, "2004-247-616", "i")).
  ?object prov:generatedAtTime ?time.
BIND(URI(concat("https://apidg.gent.be/opendata/adlib2eventstream/v1/hva/objecten?generatedAtTime=", ?time)) AS ?ldes)
} ORDER BY DESC(?object)
```

[try live](https://query.linkeddatafragments.org/#datasources=https%3A%2F%2Fstad.gent%2Fsparql&query=PREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX%20adms%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fadms%23%3E%0APREFIX%20prov%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fprov%23%3E%0A%09%09%0ASELECT%20DISTINCT%20%3Fldes%20FROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20adms%3Aidentifier%20%3Fidentifier.%0A%20%20%3Fidentifier%20skos%3Anotation%20%3Fobjectnumber.%0A%20%20FILTER%20(regex(%3Fobjectnumber%2C%20%222004-247-616%22%2C%20%22i%22)).%0A%20%20%3Fobject%20prov%3AgeneratedAtTime%20%3Ftime.%0ABIND(URI(concat(%22https%3A%2F%2Fapidg.gent.be%2Fopendata%2Fadlib2eventstream%2Fv1%2Fhva%2Fobjecten%3FgeneratedAtTime%3D%22%2C%20%3Ftime))%20AS%20%3Fldes)%0A%7D%20ORDER%20BY%20DESC(%3Fobject)%0A%0A)

## Distinct & Order by

Because of the specifications of a linked data event stream, multiple versions of records can be present. When metadata changes, the linked data event stream will publish a new version of a record, but an older version of the record still remains. To obtain solely the latest version of records, use ORDER BY to order the records chronologically (most recent versions first) and DISTINCT (to drop the following versions).

*for example*

*this query returns the first 1.000 records of the CoGhent event streams. It orders the records on publishing date. Second, it keeps only the first priref and drops any possible older versions.*

```
PREFIX purl: <http://purl.org/dc/terms/>

SELECT DISTINCT ?priref
WHERE {
SELECT ?object ?priref
WHERE { 
?object purl:isVersionOf ?priref.
} ORDER BY DESC(?object)
}
```

[try live](https://stad.gent/sparql?default-graph-uri=&query=PREFIX+purl%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fpriref%0D%0AWHERE+%7B%0D%0ASELECT+%3Fobject+%3Fpriref%0D%0AWHERE+%7B+%0D%0A%3Fobject+purl%3AisVersionOf+%3Fpriref.%0D%0A%7D+ORDER+BY+DESC%28%3Fobject%29%0D%0A%7D&format=text%2Fhtml&should-sponge=&timeout=0&signal_void=on)

## Random

You can randomize your result.

*for example*

*this query returns one random IIIF manifest from the CoGhent event streams.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?o WHERE {
  ?s cidoc:P129i_is_subject_of ?o .
  BIND(RAND() AS ?random) .
} ORDER BY ?random
LIMIT 1
```

[try live](https://stad.gent/sparql?default-graph-uri=&query=PREFIX+cidoc%3A+%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0D%0A%0D%0ASELECT+%3Fo+WHERE+%7B%0D%0A++%3Fs+cidoc%3AP129i_is_subject_of+%3Fo+.%0D%0A++BIND%28RAND%28%29+AS+%3Frandom%29+.%0D%0A%7D+ORDER+BY+%3Frandom%0D%0ALIMIT+1&format=text%2Fhtml&should-sponge=&timeout=0&signal_void=on)

The [Coghent Random Image Viewer](https://github.com/CoGhent/random_image_viewer), for example, makes use of above query.

## Union

To query multiple endpoint instead of all, it suffices to add the extra endpoint to the query.

*for example*

*this query returns the first 1.000 titles from the event streams from Design Museum Gent and het Huis van Alijn.*

```
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT ?title 
FROM <http://stad.gent/ldes/hva> 
FROM <http://stad.gent/ldes/dmg> 
WHERE { 
  ?object cidoc:P102_has_title ?title.
} 
```
[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20%3Ftitle%20%0AFROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%20%0AFROM%20%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fdmg%3E%20%0AWHERE%20%7B%20%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle.%0A%7D%20&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

However, when the query gets to complicated, it is better to use UNION.

*for example*

*this query returns 100 records with creator 'Joseph Buyens' from the event streams of het Industriemuseum en Archief Gent.*

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
[try live](http://query.linkeddatafragments.org/#datasources=https%3A%2F%2Flodi.ilabt.imec.be%2Fsparql%2Fgent&query=PREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0APREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX%20la%3A%20%3Chttps%3A%2F%2Flinked.art%2Fns%2Fterms%2F%3E%0APREFIX%20rdfs%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0A%0ASELECT%20DISTINCT%20%3Finstitution%20%3Ftitle%20%3Flabel%0AWHERE%20%7B%0A%20%20%3Fobject%20cidoc%3AP50_has_current_keeper%20%3Finstitution%20.%0A%20%20%3Fobject%20cidoc%3AP102_has_title%20%3Ftitle%20.%0A%20%20%3Fobject%20cidoc%3AP108i_was_produced_by%20%3Fproduction%20.%0A%20%20%3Fproduction%20cidoc%3AP14_carried_out_by%20%3Fmaker%20.%0A%20%20%7B%3Fmaker%20la%3Aequivalent%20%3Chttps%3A%2F%2Fstad.gent%2Fid%2Fagent%2F670003618%3E%20%7D%20UNION%20%7B%3Fmaker%20la%3Aequivalent%20%3Chttps%3A%2F%2Fstad.gent%2Fid%2Fagent%2F570025558%3E%7D%20.%0A%20%20%3Fmaker%20la%3Aequivalent%20%3Fcreator.%0A%20%20%3Fcreator%20rdfs%3Alabel%20%3Flabel.%0A%7D%20LIMIT%20100&httpProxy=http%3A%2F%2Fproxy.linkeddatafragments.org%2F)

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

     } ORDER BY DESC(?object)
  }
LIMIT 1000
OFFSET 1000
```

[try live](https://stad.gent/sparql?default-graph-uri=&query=PREFIX+purl%3A+%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0APREFIX+cidoc%3A+%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0D%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0A+++SELECT+DISTINCT+%3Fpriref+%3Flabel%0D%0A+++WHERE+%7B%0D%0A+++++SELECT+%3Fobject+%3Fpriref+%3Flabel+FROM+%3Chttp%3A%2F%2Fstad.gent%2Fldes%2Fhva%3E%0D%0A+++++WHERE+%7B+%0D%0A+++++%0D%0A+++++++%3Fobject+purl%3AisVersionOf+%3Fpriref.%0D%0A+++++++%3Fobject+cidoc%3AP128_carries+%3Fcarries.%0D%0A+++++++%3Fcarries+cidoc%3AP129_is_about+%3Fabout.%0D%0A+++++++%3Fabout+cidoc%3AP2_has_type+%3Ftype.%0D%0A+++++++%3Ftype+skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A+++++++FILTER+%28regex%28%3Flabel%2C+%22%5Ecircus%24%22%2C+%22i%22%29%29%0D%0A%0D%0A+++++%7D+ORDER+BY+DESC%28%3Fobject%29%0D%0A++%7D%0D%0ALIMIT+1000%0D%0AOFFSET+1000&format=text%2Fhtml&should-sponge=&timeout=0&signal_void=on)
