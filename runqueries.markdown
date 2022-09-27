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

[Comunica](https://comunica.dev/)

## Virtuoso Stad Gent

Queries can be run in [the virtuoso environment from Stad Gent](https://stad.gent/sparql). Results can than be exported in multiple formats.

# Run queries locally

## Comunica query engine

Installing the Comunica query engine, you can sparql locally using javascript and node.js. The default Comunica query engine that exposes most standard features is Comunica SPARQL, which uses the package name @comunica/query-sparql. Futher documentation can be found [here](https://comunica.dev/docs/query/getting_started/query_cli/). In addition, [this youtube tutorial](https://www.youtube.com/watch?v=ydpdziVNw1k) also show how to set up the comunica query engine.

## SparQL Wrapper

To sparql query in python code, the package SPARQLWrapper can be used. Documentation can be found [here](https://sparqlwrapper.readthedocs.io/en/latest/main.html). 

*for example*

```
from SPARQLWrapper import SPARQLWrapper, JSON

sparql = SPARQLWrapper("https://stad.gent/sparql")

sparql.setReturnFormat(JSON)
sparql.setQuery("""
    PREFIX cidoc: <http://www.cidoc-crm.org/cidoc-crm/>    
    SELECT ?title FROM <http://stad.gent/ldes/dmg>     
    WHERE { 
      ?object cidoc:P102_has_title ?title
    } LIMIT 100
    """)

try:
    ret = sparql.queryAndConvert()
for r in ret["results"]["bindings"]:
        print(r)
except Exception as e:
    print(e)
```

## pyLoDStorage

