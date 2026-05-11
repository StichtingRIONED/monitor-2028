# Monitor 2028

<style> <!-- Kwaliteit datasets [sync] met SLD Geoserver, gwsw-apps -->
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
  .green{background-color: #00FF37;width: 20px;}
  .green_1{background-color: #9DFF00;width: 20px;}
  .green_2{background-color: #CFFF7C;width: 20px;}
  .green_3{background-color: #DAFFBF;width: 20px;}
  .green_4{background-color: #DDFFE7;width: 20px;}
  .grey{background-color: #E2E2E2;width: 20px;}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project. Arianne Fijan is de verantwoordelijk projectleider. 
Vragen over deze website en de Monitor Gemeentelijke Watertaken 2028 kunt u stellen via arianne.fijan@rioned.org. 

# Inleiding

...

## Doel en toepassing

...

## Leeswijzer

...

# Projectbeschrijving

## Opzet en organisatie

...

## Gebruik van het GWSW

De GWSW-standaard en het bijbehorende dataplatform en applicaties is het uitgelezen middel voor het faciliteren van de gegevensverzameling voor de Monitor Gemeentelijke Watertaken 2028. Doel is zoveel mogelijk gegevens  over rioleringsobjecten (aantallen, lengtes, kenmerken) vanuit het GWSW-dataplatform te ontsluiten voor de analyses ten behoeve van de Monitor 2028.

Het GWSW is een open (linked-data) platform en gemeenten leveren periodiek hun gegevens aan op de GWSW-server.
Deze gegevens zijn met allerlei toepassingen en met zogenaamde queries (geformatteerde vragen) te gebruiken.

Op dit moment is ruim 67% van de gemeenten geregistreerd in de GWSW-database, maar er valt nog veel werk te verzetten om de kwaliteit van de aangeleverde gegevens op peil te brengen.  

Zie daarvoor ook de overzichten op [apps.gwsw.nl](https://apps.gwsw.nl)

Om de gegevenskwaliteit te verbeteren is allereerst inzicht nodig over die kwaliteit. 
Vanaf medio 2025 is een gegevenspeiling op de GWSW-server actief, daarmee kunnen gemeenten (en Stichting RIONED) de stand van zaken opvragen.
Die peiling levert een beeld van de gegevenskwaliteit, uitgedrukt in volledigheid en actualiteit.

<div class="box">
De kwaliteitmeting is operationeel, maar op dit moment is de uitspraak over het algemene kwaliteitsniveau van datasets nog gebaseerd op enkele basis-kwaliteitseisen.
In de loop der tijd wordt de meting van het algemene kwaliteitsniveau aangescherpt, dan worden meer kwaliteitseisen meegenomen.
</div>

De peiling wordt dagelijks bijgewerkt en gepubliceerd via 

* [apps.gwsw.nl - monitor]

Aan de basis van de gegevenspeiling voor de Monitor 2028 staan drie queries die gerubriceerd de gemeentelijke objectgegevens opvragen.
* Opvragen gegevens van de rioolputten
* Opvragen gegevens van de bouwwerken
* Opvragen gegevens van de rioolleidingen

[apps.gwsw.nl - monitor]: https://apps.gwsw.nl/item_monitor

[Gemengd stelsel]: http://data.gwsw.nl/GemengdStelsel
[Persleidingstelsel]: http://data.gwsw.nl/Persleidingsysteem
[Drukriolering]: http://data.gwsw.nl/Drukriolering

[Rioolput]: https://data.gwsw.nl/Rioolput
[Inspectieput]: http://data.gwsw.nl/Inspectieput
[Stuwput]: http://data.gwsw.nl/Stuwput
[Overstortput]: http://data.gwsw.nl/Overstortput

[Gemaal]: http://data.gwsw.nl/Gemaal
[Reservoir]: http://data.gwsw.nl/Reservoir
[Uitlaatconstructie]: http://data.gwsw.nl/Uitlaatconstructie
[Rioolgemaal]: http://data.gwsw.nl/Rioolgemaal

[Mechanische rioolleiding]: http://data.gwsw.nl/MechanischeRioolleiding
[Vrijverval rioolleiding]: http://data.gwsw.nl/VrijvervalRioolleiding
[Mechanische transportleiding]: http://data.gwsw.nl/MechanischeTransportleiding
[Vrijverval transportleiding]: http://data.gwsw.nl/VrijvervalTransportleiding
[Open leiding]: http://data.gwsw.nl/OpenLeiding
[Drain]: http://data.gwsw.nl/Drain
[Gemengd riool]: http://data.gwsw.nl/GemengdRiool
[Persleiding]: http://data.gwsw.nl/Persleiding
[Goot]: http://data.gwsw.nl/Goot
[Drukleiding]: http://data.gwsw.nl/Drukleiding

### Putten
Van de putten worden de subtypes van de volgende GWSW-klassen gegroepeerd (zie de kolom "groep" in de volgende tabel):
* [Rioolput]

GWSW-subtypen van putten die buiten deze groepen vallen zijn niet in de Monitor 2028 betrokken.

Een voorbeeld van het query-resultaat:

Stelsel           | groep      | type           | aantal | jaar
------------------|------------|----------------|--------|-----
[Gemengd stelsel] | [Rioolput] | [Rioolput]     | 1      | 1980
[Gemengd stelsel] | [Rioolput] | [Inspectieput] | 7      | 1970
[Gemengd stelsel] | [Rioolput] | [Stuwput]      | 1      | 1970
[Gemengd stelsel] | [Rioolput] | [Overstortput] | 1      | 1970

### Bouwwerken
Van de bouwwerken worden de subtypes van de volgende GWSW-klassen gegroepeerd (zie de kolom "groep" in de volgende tabel):
* [Gemaal]
* [Reservoir]
* [Uitlaatconstructie]

GWSW-subtypen van bouwwerken die buiten deze groepen vallen zijn niet in de Monitor 2028 betrokken.

Een voorbeeld van het query-resultaat:

Stelsel           | groep    | type          | aantal | jaar
------------------|----------|---------------|--------|-----
[Gemengd stelsel] | [Gemaal] | [Rioolgemaal] | 1      | 1980

### Leidingen
Van de leidingen worden de subtypes van de volgende GWSW-klassen gegroepeerd (zie de kolom "groep" in de volgende tabel):
* [Mechanische rioolleiding]
* [Vrijverval rioolleiding]
* [Mechanische transportleiding]
* [Vrijverval transportleiding]
* [Open leiding]
* [Drain]

GWSW-subtypen van leidingen die buiten deze groepen vallen zijn niet in de Monitor 2028 betrokken.

Een voorbeeld van het query-resultaat:

Stelsel              | groep                          | type            | aantal | jaar | Lining | somLengte
---------------------|--------------------------------|-----------------|--------|------|--------|----------
[Drukriolering]      | [Mechanische rioolleiding]     | [Drukleiding]   | 1      |      |        | 155.67
[Gemengd stelsel]    | [Vrijverval rioolleiding]      | [Gemengd riool] | 10     | 1970 |        | 392.02
[Gemengd stelsel]    | [Vrijverval rioolleiding]      | [Gemengd riool] | 1      | 1980 |        | 41.0
[Gemengd stelsel]    | [Vrijverval rioolleiding]      | [Gemengd riool] | 1      | 1970 | ja     | 38.0
[Persleidingstelsel] | [Mechanische transportleiding] | [Persleiding]   | 2      |      |        | 264.0
[Gemengd stelsel]    | [Open leiding]                 | [Goot]          | 1      |      |        | 30.0
[Gemengd stelsel]    | [Drain]                        | [Drain]         | 1      | 1970 |        | 42.0


### Bepaling gegevenskwaliteit

GWSW Apps meet dagelijks de kwaliteit voor alle NL-gemeenten en presenteert deze op [apps.gwsw.nl - monitor].
Die site toont op aanvraag ook de details van de kwaliteitsmeting per gemeente. 
Voor de meting zijn een aantal kwaliteitseisen geformuleerd. Het bereikte kwaliteitsniveau per kwaliteitseis wordt uitgedrukt in drie kleuren:

Niveau | Kleur                                                       | Kwaliteit
-------|-------------------------------------------------------------|-------------------
1      | <span class="green">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>   | Hoog
2      | <span class="green_2">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | Gemiddeld
3      | <span class="green_4">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | Laag

De gemeentelijke gegevens worden getoetst aan de volgende kwaliteitseisen:

**Kwaliteitseisen algemeen**  

id          | melding                    | gewicht | eh            | <div class="green">&nbsp;</div> | <div class="green_2">&nbsp;</div> | <div class="green_4">&nbsp;</div>
------------|----------------------------|---------|---------------|---------------------------------|-----------------------------------|----------------------------------
actualiteit | Dataset voldoende actueel? | 1       | jaar             | <1                              | <3                                | >=3
validatie   | Validatie dataset-upload   | 3       | aantal fouten | <1                              | <6                                | >=6

**Kwaliteitseisen putten**  

id           | melding                          | gewicht | eh | <div class="green">&nbsp;</div> | <div class="green_2">&nbsp;</div> | <div class="green_4">&nbsp;</div>
-------------|----------------------------------|---------|----|---------------------------------|-----------------------------------|----------------------------------
aantal       | Aantal putten/inwoners           | 3       | %  | >5 <100                         | >0                                | =0
filter       | Aantal putten/aantal-ongefilterd | 0       | %  | >95                             | >=80                              | <80
jaar         | Aanlegjaar aanwezig?             | 0       | %  | >=5                             | >0                                | =0
Inspectieput | Inspectieputten aanwezig?        | 0       | %  | >=85                            | >=80                              | <80

**Kwaliteitseisen bouwwerken**  

id     | melding                              | gewicht | eh | <div class="green">&nbsp;</div> | <div class="green_2">&nbsp;</div> | <div class="green_4">&nbsp;</div>
-------|--------------------------------------|---------|----|---------------------------------|-----------------------------------|----------------------------------
filter | Aantal bouwwerken/aantal-ongefilterd | 0       | %  | >95                             | >=80                              | <80
jaar   | Aanlegjaar aanwezig?                 | 0       | %  | >=95                            | >=80                              | <80

**Kwaliteitseisen leidingen**  

id                     | melding                             | gewicht | eh | <div class="green">&nbsp;</div> | <div class="green_2">&nbsp;</div> | <div class="green_4">&nbsp;</div>
-----------------------|-------------------------------------|---------|----|---------------------------------|-----------------------------------|----------------------------------
aantal                 | Aantal leidingen/inwoners           | 3       | %  | >5 <100                         | >0                                | =0
filter                 | Aantal leidingen/aantal-ongefilterd | 0       | %  | >95                             | >=80                              | <80
jaar                   | Aanlegjaar aanwezig?                | 0       | %  | >=95                            | >=80                              | <80
lengte                 | Gemiddelde leidinglengte            | 0       | m  | >=30                            | >=20                              | <20
VrijvervalRioolleiding | Vrijverval rioolleiding aanwezig?   | 0       | %  | >=80                            | >=70                              | <70


<mark><b>Optionele kwaliteitseisen (verder uitwerken)</b></mark>

* Past het objecttype bij het stelseltype?
* Is het objecttype concreet genoeg? Objecten binnen GWSW-filter analyseren, kunnen te abstract zijn. Toetsing op aantal-ongefilterd kan dan vervallen.
* Upload-validatie verder verfijnen: wordt GGN Monitor

### Algemene kwaliteit per gemeente

De uitspraak over de algemene kwaliteit is gebaseerd op de meetresultaten per kwaliteitseis.

<div class="box">
<i>Stapsgewijze aanscherping gewenste kwaliteitniveau</i><br/><br/>
Het is de bedoeling de kwaliteitsmeting in de komende jaren geleidelijk aan te scherpen.
De op dit moment gebruikte kwaliteitseisen voor bepaling van de algemene kwaliteit per gemeente hebben een **gewicht groter dan 0** in het overzicht hiervoor.
</div>

Op dit moment (vanaf 1 mei 2026) worden alleen enkele basiskwaliteiten gemeten.

Voor de algemene dataset-kwaliteit hanteren we vijf niveaus/groenwaarden (van hoog naar laag): 
&nbsp;&nbsp;<span class="green">&nbsp;&nbsp;&nbsp;</span> <span class="green_1">&nbsp;&nbsp;&nbsp;</span> <span class="green_2">&nbsp;&nbsp;&nbsp;</span> <span class="green_3">&nbsp;&nbsp;&nbsp;</span> <span class="green_4">&nbsp;&nbsp;&nbsp;</span>

Het algemene kwaliteitniveau is gebaseerd op het gemiddelde van de niveaus per kwaliteitseis, rekening houden met het gewicht per kwaliteiteis.

* at_1 = sommatie gewicht van kwaliteitseisen met niveau 1 &nbsp;&nbsp;<span class="green">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
* at_2 = sommatie gewicht van kwaliteitseisen met niveau 2 &nbsp;&nbsp;<span class="green_2">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
* at_3 = sommatie gewicht van kwaliteitseisen met niveau 3 &nbsp;&nbsp;<span class="green_4">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
* avg = gemiddelde waarde tussen hoog (=0) en laag (=2) = ((at_1 * 0) + (at_2 * 1) + (at_3 * 2)) / (at_1 + at_2 + at_3)

Algemene kwaliteitniveau van hoog (=0) naar laag (=4) = (avg / 2) * 4
&nbsp;&nbsp;<span class="green">&nbsp;&nbsp;&nbsp;</span> <span class="green_1">&nbsp;&nbsp;&nbsp;</span> <span class="green_2">&nbsp;&nbsp;&nbsp;</span> <span class="green_3">&nbsp;&nbsp;&nbsp;</span> <span class="green_4">&nbsp;&nbsp;&nbsp;</span>

