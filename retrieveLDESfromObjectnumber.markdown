---
layout: page
title: LDES objects from object numbers
parent: API
nav_order: 4
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## **Retrieve link to LDES**

Click [here](https://getldes.herokuapp.com/linktoldes/getldes/) to retrieve the link to most recently published LDES version. 


## **Retrieve object from LDES via URL manually**

There is a workaround to retrieve the page of the event stream on which the latest state of an object is published. Precondition for this method to be used is that the object number is known. 

**Step 1**: open the IIIF manifest of the object from which you want to retrieve the event stream. This can be done via the corresponding object number (https://api.collectie.gent/iiif/presentation/v2/manifest/{PUBLISHING_INSTITUTION}:{OBJECT_NUMBER}).


For example: [https://api.collectie.gent/iiif/presentation/v2/manifest/dmg:1987-1049](https://api.collectie.gent/iiif/presentation/v2/manifest/dmg:1987-1049)


**Step 2**: from within the manifest copy the timestamp under "rendering", "@id"
https://stad.gent/id/mensgemaaktobject/{PUBLISHING_INSTITUTION}/{PRIREF}/{TIMESTAMP}


<img width="1416" alt="Schermafbeelding 2022-05-16 om 16 21 43" src="https://user-images.githubusercontent.com/43210443/168614557-e9ad6a79-6cba-46ae-8162-53f642f22053.png">


For the given example: "2022-06-10T00:19:02.777Z"

**Step 3**: paste the timestamp in the correct LDES: https://apidg.gent.be/opendata/adlib2eventstream/v1/{PUBLISHING_INSTITUTION}/{LDES}?generatedAtTime= 
 {PASTE HERE}
 
 
 For the given example: [https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten?generatedAtTime=2022-06-10T00:19:02.777Z](https://apidg.gent.be/opendata/adlib2eventstream/v1/dmg/objecten?generatedAtTime=2022-06-10T00:19:02.777Z)
