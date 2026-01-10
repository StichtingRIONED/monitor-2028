# Monitor 2028

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
  .green{background-color: #44FF70;width: 20px;}
  .yellow{background-color: #FFC300;width: 20px;}
  .orange{background-color: #FF554C;width: 20px;}
  .purple{background-color: #7E6DFF;width: 20px;}
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

Zie daarvoor ook de overzichten op [apps.gwsw.nl - overzicht datasets](https://apps.gwsw.nl/item_validate_nl)

Om de gegevenskwaliteit te verbeteren is allereerst inzicht nodig over die kwaliteit. 
Vanaf medio 2025 is een gegevenspeiling op de GWSW-server actief, daarmee kunnen gemeenten (en Stichting RIONED) de stand van zaken opvragen.
Die peiling levert een beeld van de gegevenskwaliteit, uitgedrukt in volledigheid en actualiteit.

<mark><b>
DE KWALITEITSMETING IS IN CONCEPT OPERATIONEEL MAAR DE KWALITEITSEISEN EN UITSPRAKEN  
OVER DE KWALITEIT ZIJN NOG NIET REALISTISCH.
</b></mark>

De peiling wordt dagelijks bijgewerkt en gepubliceerd via 

* [apps.gwsw.nl - status monitor]

Aan de basis van de gegevenspeiling voor de Monitor 2028 staan drie queries die gerubriceerd de gemeentelijke objectgegevens opvragen.
* Opvragen gegevens van de rioolputten
* Opvragen gegevens van de bouwwerken
* Opvragen gegevens van de rioolleidingen

[apps.gwsw.nl - status monitor]: https://apps.gwsw.nl/item_status_monitor

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

Met GWSW-Apps wordt een indicatie van de gegevenskwaliteit per gemeente gegeven. De kwaliteit wordt uitgedrukt in vier kleuren:

Kleur                                                      | Kwaliteit
-----------------------------------------------------------|-------------------
<span class="green">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>  | Gegevens in orde
<span class="yellow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | Er zijn nog fouten
<span class="orange">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | Onvoldoende
<span class="purple">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | Fout in analyse

Zoals gezegd meet GWSW Apps dagelijks de kwaliteit voor alle NL-gemeenten en presenteert deze op [apps.gwsw.nl - status monitor].
Die site toont op aanvraag ook de details van de kwaliteitsmeting per gemeente.

<mark><b>
DE KWALITEITSMETING IS IN CONCEPT OPERATIONEEL MAAR DE KWALITEITSEISEN WORDEN NOG VASTGESTELD
</b></mark>

Voor de bepaling van de kwaliteit worden de query-resultaten getoetst aan een serie kwaliteitseisen.

De nu actieve kwaliteitseisen (de globale proefneming):

**Kwaliteitseisen algemeen**  

id          | mess                       | weight | eh            | <div class="green">&nbsp;</div> | <div class="yellow">&nbsp;</div> | <div class="orange">&nbsp;</div>
------------|----------------------------|--------|---------------|---------------------------------|----------------------------------|---------------------------------
actualiteit | Dataset voldoende actueel? | 3      | y             | <1                              | <3                               | >=3
validatie   | Validatie dataset-upload   | 3      | aantal fouten | <1                              | <6                               | >=6

**Kwaliteitseisen putten**  

id           | mess                             | weight | eh | <div class="green">&nbsp;</div> | <div class="yellow">&nbsp;</div> | <div class="orange">&nbsp;</div>
-------------|----------------------------------|--------|----|---------------------------------|----------------------------------|---------------------------------
aantal       | Aantal putten/inwoners           | 3      | %  | >5 <100                         | >0                               | =0
filter       | Aantal putten/aantal-ongefilterd | 1      | %  | >95                             | >=80                             | <80
jaar         | Aanlegjaar aanwezig?             | 1      | %  | >=5                             | >0                               | =0
Inspectieput | Inspectieputten aanwezig?        | 1      | %  | >=85                            | >=80                             | <80

**Kwaliteitseisen bouwwerken**  

id     | mess                                 | weight | eh | <div class="green">&nbsp;</div> | <div class="yellow">&nbsp;</div> | <div class="orange">&nbsp;</div>
-------|--------------------------------------|--------|----|---------------------------------|----------------------------------|---------------------------------
filter | Aantal bouwwerken/aantal-ongefilterd | 1      | %  | >95                             | >=80                             | <80
jaar   | Aanlegjaar aanwezig?                 | 1      | %  | >=95                            | >=80                             | <80

**Kwaliteitseisen leidingen**  

id                     | mess                                | weight | eh | <div class="green">&nbsp;</div> | <div class="yellow">&nbsp;</div> | <div class="orange">&nbsp;</div>
-----------------------|-------------------------------------|--------|----|---------------------------------|----------------------------------|---------------------------------
aantal                 | Aantal leidingen/inwoners           | 3      | %  | >5 <100                         | >0                               | =0
filter                 | Aantal leidingen/aantal-ongefilterd | 1      | %  | >95                             | >=80                             | <80
jaar                   | Aanlegjaar aanwezig?                | 1      | %  | >=95                            | >=80                             | <80
lengte                 | Gemiddelde leidinglengte            | 1      | m  | >=30                            | >=20                             | <20
VrijvervalRioolleiding | Vrijverval rioolleiding aanwezig?   | 1      | %  | >=80                            | >=70                             | <70

**Optionele kwaliteitseisen (nog niet operationeel)**  

* Past het objecttype bij het stelseltype?
* ...

### Algemene kwaliteit per gemeente

De uitspraak over de algemene kwaliteit is gebaseerd op de meetresultaten per kwaliteitseis.

De formule daarvoor is: 

<mark><b>
DE FORMULE VOOR DE ALGEMENE UITSPRAAK OVER DE DATASET-KWALITEI WORDT NOG UITGEWERKT
</b></mark>

* atPaars = (aantal * gewicht) kwaliteiten Paars
* atRood = (aantal * gewicht) kwaliteiten Rood
* atOranje = (aantal * gewicht) kwaliteiten Oranje
* at = aantal kwaliteiten Paars + Rood + Oranje + Groen  


* Als **atPaars / at > 0.01**: Dataset-kwaliteit = <span class="purple">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> 
* Of als **(atPaars + atRood) / at > 0.2**: Dataset-kwaliteit = <span class="orange">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> 
* Of als **(atPaars + atRood + atOranje) / at > 0.3**: Dataset-kwaliteit = <span class="yellow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> 
* Overig: Dataset-kwaliteit = <span class="green">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>


