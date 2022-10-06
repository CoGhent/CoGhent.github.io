---
layout: page
title: ldes-client
parent: API
nav_order: 2
---

# actor-init-ldes-client

The actor-init-ldes-client can be used to harvest the published eventstreams via the command line interface (CLI) or can be setup within an application. Full documentation on the actor-init-ldes-client can be found [here](https://github.com/TREEcg/event-stream-client/tree/main/packages/actor-init-ldes-client). 

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Setup

Make sure you have [Node.js](https://nodejs.org/en/) installed. Open the Node.js command prompt. Install the actor-init-ldes-client npm package:

```
npm install -g @treecg/actor-init-ldes-client
```

Run a command in the Node.js command prompt to harvest to harvest a certain event stream

*for example*

```
actor-init-ldes-client  https://apidg.gent.be/opendata/adlib2eventstream/v1/hva/objecten
```

The links to the event streams can be found [here](https://coghent.github.io/LDES/)

It is possible to add multiple parameters to your command:

| Parameter  | Description | Possible values |
| ------------- | ------------- | ------------- |
| pollingInterval | Number of milliseconds before refetching uncacheable fragments  | for example: 5000 |
| mimeType  | the MIME type of the output  | application/ld+json, text/turtle... |
| context  | path to a file with the JSON-LD context you want to use when MIME type is application/ld+json  | for example: ./context.jsonld |
| fromTime  | datetime to prune relations that have a lower datetime value | for example: 2020-01-01T00:00:00 |
| emitMemberOnce  | whether to emit a member only once, because collection contains immutable version objects.  | true / false |
| disableSynchronization  | whether to disable synchronization or not (by default set to "false", syncing is enabled) | true / false |
| disableFraming  | whether to disable JSON-LD framing when mimeType is 'application/ld+json' or when representation is 'Object' (by default set to "false"). Value can be set to "true" or "false" | true / false |
| dereferenceMembers | whether to dereference members, because the collection pages do not contain all information (by default: false). | true / false |
| requestsPerMinute | how many requests per minutes may be sent to the same host (optional) | any number |
| loggingLevel | The detail level of logging; useful for debugging problems. (default: info)| 'error', 'warn', 'info', 'verbose', 'debug', 'silly' |
| processedURIsCount | The maximum number of processed URIs (members and fragments) that remain in the cache. (default: 10000) | any number |


*for example*

```
actor-init-ldes-client --pollingInterval 5000 --mimeType application/ld+json --context context.jsonld --fromTime 2021-02-03T15:48:12.309Z --emitMemberOnce true --disablePolling true https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten
```

## Use locally


Install the npm package on the location where you want to run the script. Copy the commmand line below in the CLI; 

```
npm install -g @treecg/actor-init-ldes-client
```

In order to use it as a library, you can leave out the **-g**.

## Use context

Save the context (from the code below) locally. 

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


The following commands can be used to fetch the event streams. Make sure to exchange the FILEPATH_TO_CONTEXT to the path containing the context file as shown above. 

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

## Save result

To save the result add following line to your command:

```
> PATH_TO_DIRECTORY\output.json
```

A json file (output.json) will be saved in the directory of your choice.
