---
layout: page
title: NPM Client
parent: API
nav_order: 2
---

# actor-init-ldes-client

The actor-init-ldes-client can be used to harvest the published eventstreams via the command line interface (CLI) or can be setup within an application. Full documentation on the actor-init-ldes-client can be found [here](https://github.com/TREEcg/event-stream-client/tree/main/packages/actor-init-ldes-client). 

## setup

1. to use the actor-init-ldes-client first install the npm package on the location where you want to run the script. To do this copy the commmand line below in the CLI; 

```
npm install -g @treecg/actor-init-ldes-client
```
2. save the context (from the code below) locally. 

```
{   "@context": [
                "https://apidg.gent.be/opendata/adlib2eventstream/v1/context/cultureel-erfgoed-object-ap.jsonld",
		        "https://apidg.gent.be/opendata/adlib2eventstream/v1/context/persoon-basis.jsonld",
		        "https://apidg.gent.be/opendata/adlib2eventstream/v1/context/cultureel-erfgoed-event-ap.jsonld",
		        "https://apidg.gent.be/opendata/adlib2eventstream/v1/context/organisatie-basis.jsonld",
      {
          "dcterms:isVersionOf": {
              "@type": "@id"
          },
          "prov": "http://www.w3.org/ns/prov#",
          "skos": "http://www.w3.org/2004/02/skos/core#",
          "label": "http://www.w3.org/2000/01/rdf-schema#label",
          "opmerking": "http://www.w3.org/2004/02/skos/core#note",

          "cest": "https://www.projectcest.be/wiki/Publicatie:Invulboek_objecten/Veld/"
      }
  ]
}
```
## usage 

after installing the npm package the following commands can be used to fetch the event streams. Make sure to exchange the FILEPATH_TO_CONTEXT to the path containing the context file as shown above. 

```
// Design Museum Gent (objects)

actor-init-ldes-client --pollinInterval 5000 --mimeType application/ld+json --context FILEPATH_TO_CONTEXT --fromTime "2022-05-00T00:00:00.309Z" --emitMemberOnce false --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten

// Archief Gent (objects)

actor-init-ldes-client --pollinInterval 5000 --mimeType application/ld+json --context FILEPATH_TO_CONTEXT --fromTime "2022-05-00T00:00:00.309Z" --emitMemberOnce false --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/archiefgent/objecten

// STAM (objects)

actor-init-ldes-client --pollinInterval 5000 --mimeType application/ld+json --context FILEPATH_TO_CONTEXT --fromTime "2022-05-00T00:00:00.309Z" --emitMemberOnce false --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/stam/objecten

// Huis van Alijn (objects). 

actor-init-ldes-client --pollinInterval 5000 --mimeType application/ld+json --context FILEPATH_TO_CONTEXT --fromTime "2022-05-00T00:00:00.309Z" --emitMemberOnce false --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/hva/objecten

Industriemuseum (objects) 

actor-init-ldes-client --pollinInterval 5000 --mimeType application/ld+json --context FILEPATH_TO_CONTEXT --fromTime "2022-05-00T00:00:00.309Z" --emitMemberOnce false --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/im/objecten
```

***
