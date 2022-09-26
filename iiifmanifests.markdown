---
layout: page
title: IIIF Manifests
permalink: /IIIF Manifests/
nav_order: 4
---

# **IIIF Manifests** 


Images of published objects from the 5 cultural heritage organisations and their corresponding technical metadata are published as IIIF manifests. 

|abbreviation|publishing organisation|iiif manifest|
|---------|----------|-----------|
|dmg|Design Museum Gent|https://api.collectie.gent/iiif/presentation/v2/manifest/dmg:*objectnumber*|
|hva|Huis van Alijn|https://api.collectie.gent/iiif/presentation/v2/manifest/hva:*objectnumber*|
|industriemuseum|Industriemuseum|https://api.collectie.gent/iiif/presentation/v2/manifest/industriemuseum:*objectnumber*|
|stam|STAM|https://api.collectie.gent/iiif/presentation/v2/manifest/stam:*objectnumber*|
|archiefgent|Archief Gent|https://api.collectie.gent/iiif/presentation/v2/manifest/|archiefgent:*objectnumber*|

The IIIF manifest contains the link to the image as well as additional data such as licence of the image, format of the image, size of the image, source of the image and so on.

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
