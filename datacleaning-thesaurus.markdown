---
layout: page
title: Datacleaning - thesaurus 
parent: Datacleaning
nav_order: 1
---

# THESAURUS 

## 1. Zoeken 

Typ het woord dat je wil controleren in de zoekfunctie op Axiell of Adlib

**Tip**: als je bv. gloeilamp wil controleren zoek je best *gloeilamp* zodat je meteen ook kan checken of er meervoudsvormen of afgeleiden in de thesaurus staan. Wil je heel volledig controleren kan je ook op *lamp* of *gloei* zoeken. 

## 2. Gekoppelde records bekijken 

Open een term uit de lijst zoekresultaten en ga in het menu naar “beeld” en klik vervolgens op “link overzicht”, nu komt er een pop-up scherm dat toont hoeveel records er aan de term gekoppeld zijn en aan welke velden de term gekoppeld is.

![](images/thesaurus_00.png)
![](images/thesaurus_01.png)
![](images/thesaurus_02.png)

**Tip**: deze functie werkt voorlopig enkel in Adlib en niet in Axiell Tip: Door op het "+"-teken te klikken kan je het nummer of priref van het record zien waaraan de term is gekoppeld. Je kan dit nummer zoeken in Adlib of Axiell via “ %0 = ”

## 3. Term zonder gekoppelde records 

Hangt er geen enkel record aan de term? Controleer dan of er bij “use” een andere term staat. Zo ja: verander de status van het de term naar “non-descriptor”. Staat er geen term? Controleer dan eerst of er een vervangende term in de thesaurus zit. Is dit niet het geval, dan kan de term uit de thesaurus verwijderd worden.

![](images/thesaurus_03.png)

**Tip**: wanneer je een lange lijst termen wil aanpakken is het gemakkelijk om bovenaan het record te markeren wanneer het kan verwijderd worden. Daarna kan je in één keer alle gemarkeerde records verwijderen.
**Tip**: een term toevoegen bij “use” of “use for” kan voorlopig enkel in adlib en niet in axiell.

## 4.  Term met gekoppelde records 

Controleer of de term uniek is en verander de status van de term naar “descriptor”

## 5.  Koppelen met externe authoriteiten 

Kijk of de term opgenomen is in AAT, Wikidata, of, in het geval van een geografisch trefwoord, TGN. Kopieer de URI en de scope note als deze beschikbaar is. Voeg de bron als volgt toe:

### AAT:
![](images/thesaurus_04.png)

### Wikidata:
![](images/thesaurus_05.png)

### TGN:
![](images/thesaurus_06.png)

**Tip**: Als je het veld “Bron” aanklik, geeft Axiell een drop down menu van de verschillende opties die eerder door jou gebruikt zijn, dan hoef je niet telkens de hele URI te kopiëren en te plakken. In Adlib kan dit helaas niet.

**Je vindt de nummers als volgt:**

![](images/thesaurus_07.png)
![](images/thesaurus_08.png)
![](images/thesaurus_09.png)

# Casussen 

## 1.    In de thesaurus staat een term zowel in enkelvoud als meervoud

In sommige gevallen is het nodig dat zowel de meervoudsvorm als de enkelvoudsvorm in de thesaurus opgenomen zijn, ga eerst na of dit het geval is. Zo niet, volg dan het onderstaande stappenplan.
- Controleer via het linkoverzicht aan welke term het meest records hangen
- Zoek bij objecten in eigen beheer naar de records waaraan de minst gebruikte term hangt; dit kan op twee manieren:
  - Kijk in het linkoverzicht naar het veld waarin de term zich bevindt 
  - Zoek vervolgens via de zoekmodus naar deze records 
  - Het linkoverzicht toont ook de priref van het record, in geavanceerd zoeken kan je hierop zoeken via “ %0 = ” 
- Via “zoek en vervang” kan je alle records aan de meest gebruikte term koppelen
- Hangen er ongeveer evenveel records aan de term? Kies dan de voor de meervoudsvorm, deze staat in AAT altijd als de geprefereerde term

## 2.    In de thesaurus staan synoniemen

- Gebruik hier de velden “use” en “used for”
- Controleer in AAT welke term geprefereerd wordt

![](images/thesaurus_10.png)

-  Schrijf de geprefereerde term in het veld “use” bij het synoniem. Bij de juiste term verschijnt het synoniem automatisch in het veld “used for”

**Tip: je kan meerdere termen toevoegen bij “used for”, dit zorgt ervoor dat je wel nog kan zoeken op deze termen maar dat deze niet meer actief kunnen gebruikt worden in adlib**

- Adlib vervangt in de gekoppelde records automatisch de oude term door de nieuwe, geprefereerde term
- Verander bij de termen die niet langer actief zullen gebruikt worden de status naar “non-descriptor”

## 3.    In de thesaurus staan identieke termen

- Controleer via het linkoverzicht aan welke term het meest records hangen
- Verander de status van de meest gebruikte term naar “descriptor”
- koppel alle records aan de meest gebruikte term, dit kan op twee manieren:
  - zoek de gekoppelde records één voor één via de priref die je vind in het linkoverzicht en vervang de term
  - gebruik de velden “use” en “used for”; Adlib koppelt dan automatisch de records aan de term die je kiest, hierna kan je de overbodige term verwijderen






