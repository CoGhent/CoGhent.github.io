---
layout: page
title: IIIF Manifests
permalink: /IIIF Manifests/
nav_order: 4
---

# **IIIF Manifests** 

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## IIIF manifest links

Images of published objects from the 5 cultural heritage organisations and their corresponding technical metadata are published as IIIF manifests. 

|abbreviation|publishing organisation|iiif manifest|
|---------|----------|-----------|
|dmg|Design Museum Gent|https://api.collectie.gent/iiif/presentation/v2/manifest/dmg:*objectnumber*|
|hva|Huis van Alijn|https://api.collectie.gent/iiif/presentation/v2/manifest/hva:*objectnumber*|
|industriemuseum|Industriemuseum|https://api.collectie.gent/iiif/presentation/v2/manifest/industriemuseum:*objectnumber*|
|stam|STAM|https://api.collectie.gent/iiif/presentation/v2/manifest/stam:*objectnumber*|
|archiefgent|Archief Gent|https://api.collectie.gent/iiif/presentation/v2/manifest/archiefgent:*objectnumber*|

The IIIF manifest contains the link to the image as well as additional data such as licence of the image, format of the image, size of the image, source of the image and so on.

## Image not publicly available

Not every heritage object published in the event streams have images or images that are publicly available. Certain images are not publicly available due to copyright restrictions. The correspoding technical metadata in the IIIF manifest is however still accessible. Accessing the IIIF manifests of objects without images will result in the following error: 

```
message:	"You don't have permission to access this resource"
```

You can check if there is a IIIF manifest by using the following python code:  

```
try:
    # code that may cause errors
except:
    # code that handle exceptions
else:
    # code that executes when no exception occurs  
```  

E.g.:  
*#cogentid# equals instelling:objectnumber (dmg:objectnumber, hva:objectnumber, industriemuseum:objectnumber, stam:objectnumber, archiefgent:objectnumber)* 
```
def image(request):
    iiif_manifest = "https://api.collectie.gent/iiif/presentation/v2/manifest/#cogentid#"

    try:
        response = urlopen(manifest)
    except ValueError:
        print('no image found')
    except HTTPError:
        print('no image found')
    else:
        data_json = json.loads(response.read())
        image_uri = data_json["sequences"][0]['canvases'][0]["images"][0]["resource"]["@id"]
        print(image_uri) 
```  

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
