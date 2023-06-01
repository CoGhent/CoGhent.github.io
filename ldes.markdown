---
layout: page
title: CoGhent Data
permalink: /LDES/
has_children: true
nav_order: 2
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>


# CoGhent Data
## LDES (Linked Data Event Stream)

Collections of Ghent published its data using Linked Data Event Streams. A Linked Data Event Stream is a collection of versioned objects (a version is like an event) and can be updated anytime at their own pace (slow and fast data). This way, consumers can easily discover and harvest the latest changes.

If you are new to the concept of Linked Data Event Stream or Linked Data, [this short training](https://academy.europa.eu/courses/publishing-data-with-linked-data-event-streams-why-and-how) introduces the main concepts.

## CoGhent Linked Data Event Streams

Collections of Ghent published multiple Linked Data Event streams containing information on objects from five cultural heritage organizations located in the city of Ghent: 
- [Design Museum Gent](https://coghent.github.io/dmg.html)
- [Huis van Alijn](https://coghent.github.io/hva.html)
- [Industriemuseum](https://coghent.github.io/im.html)
- [STAM](https://coghent.github.io/stam.html)
- [Archief Gent](https://coghent.github.io/ag.html)

The Linked Data Event Streams are enriched with links to IIIF manifests containing the images of the published objects. 

In addition three extra event streams have been published: 
- [Agent lists](https://coghent.github.io/thesaurus.html) from all five institutions 
- [Thesaurus](https://coghent.github.io/thesaurus.html) (concepts) from all five institutions
- [Exhibition data](https://coghent.github.io/exhibitiondmg.html) from Design Museum Gent.

## Using the data

API

The data from the Linked Data Event Stream can be obtained by using the actor-init-ldes-client to harvest the event streams into json or json-ld format. More info can be found [https://coghent.github.io/npmclient.html](here)

SparQL Endpoint

Another way to access the data in the Linked Data Event Streams is by using SparQL queries to obtain certain sets of data. More info can be found [https://coghent.github.io/SparQl%20Endpoint/](here)

## Terms of use

### Metadata

All metadata contained in the Linked Data Event Streams is published under a CC0 license.

### Images

Images are published under multiple licenses. The license of an image can be found in the IIIF manifests. 

*for example*

![image](https://user-images.githubusercontent.com/78723853/202168875-68c163d5-4d57-4f3a-96a4-716d618395f0.png)

The licenses used for published images in the Collections of Ghent are either Creative Common licenses or Rights Statements. Please consult the documentation for further explanation of the terms of use:
- Creative Commons: [https://creativecommons.org/](https://creativecommons.org/)
- Rights Statements: [https://rightsstatements.org/en/](https://rightsstatements.org/en/)


