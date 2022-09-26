---
layout: page
title: Run queries
parent: SparQL Endpoint
nav_order: 4
---

# Run Queries

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Run queries in browser

queries can be run directly in the browser using services such as Comunica and Virtuoso. 

## Comunica

[Comunica](https://comunica.dev/)'s Link traversal feature can be used to directly fetch links to the IIIF image API when querying the SPARQL endpoint. 

```
PREFIX oa: <http://www.w3.org/ns/oa#>
PREFIX sc: <http://iiif.io/api/presentation/2#>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>

SELECT *

WHERE {
  ?s a cidoc:E22_Man-Made_Object ;
     cidoc:P129i_is_subject_of [
      sc:hasSequences/rdf:rest*/rdf:first [
    		sc:hasCanvases/rdf:rest*/rdf:first [
          		sc:hasImageAnnotations/rdf:rest*/rdf:first [
            			oa:hasBody ?body
        		]
      		]
    	]
  	]
}
```

[try live](https://comunica.github.io/comunica-feature-link-traversal-web-clients/builds/follow-match-query/#datasources=https%3A%2F%2Fapidg.gent.be%2Fopendata%2Fadlib2eventstream%2Fv1%2Fdmg%2Fobjecten%3FgeneratedAtTime%3D2022-08-25T00%3A00%3A33.474Z&query=PREFIX%20oa%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Foa%23%3E%0APREFIX%20sc%3A%20%3Chttp%3A%2F%2Fiiif.io%2Fapi%2Fpresentation%2F2%23%3E%0APREFIX%20dc%3A%20%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Felements%2F1.1%2F%3E%0APREFIX%20prov%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fprov%23%3E%0APREFIX%20cidoc%3A%20%3Chttp%3A%2F%2Fwww.cidoc-crm.org%2Fcidoc-crm%2F%3E%0A%0ASELECT%20*%0A%0AWHERE%20%7B%0A%20%20%3Fs%20a%20cidoc%3AE22_Man-Made_Object%20%3B%0A%20%20%20%20%20cidoc%3AP129i_is_subject_of%20%5B%0A%20%20%20%20%20%20sc%3AhasSequences%2Frdf%3Arest*%2Frdf%3Afirst%20%5B%0A%20%20%20%20%09%09sc%3AhasCanvases%2Frdf%3Arest*%2Frdf%3Afirst%20%5B%0A%20%20%20%20%20%20%20%20%20%20%09%09sc%3AhasImageAnnotations%2Frdf%3Arest*%2Frdf%3Afirst%20%5B%0A%20%20%20%20%20%20%20%20%20%20%20%20%09%09%09oa%3AhasBody%20%3Fbody%0A%20%20%20%20%20%20%20%20%09%09%5D%0A%20%20%20%20%20%20%09%09%5D%0A%20%20%20%20%09%5D%0A%20%20%09%5D%0A%7D).

## Virtuoso Stad Gent

https://stad.gent/sparql

# Run queries locally

## Comunica query engine

## SparQL Wrapper

## pyLoDStorage
