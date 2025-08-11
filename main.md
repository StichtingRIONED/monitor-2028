# Monitor 2028

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
  .kwalGreen{background-color: #44FF70;}
  .kwalYellow{background-color: #FFC300;}
  .kwalOrange{background-color: #FF554C;}
  .kwalPurple{background-color: #7E6DFF;}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project, Arianne Fijan is de verantwoordelijk projectleider. 
Vragen over deze website en de Monitor 2028 kunt u stellen via arianne.fijan@rioned.org. 

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

Het GWSW is het uitgelezen middel voor het uitvoeren van een gegevens-peiling voor de Monitor 2028. 

Het GWSW is een open (linked-data) platform vanwaar gegevens met zogenaamde queries (geformatteerde vragen) worden opgevraagd.
Gemeenten leveren periodiek hun gegevens aan op de GWSW Server.  

Op dit moment is ruim 67% van de gemeenten geregistreerd in de GWSW-database, maar er valt nog veel werk te verzetten om de kwaliteit van de aangeleverde gegevens op peil te brengen.  

Zie daarvoor ook de overzichten op [apps.gwsw.nl - overzicht datasets](https://apps.gwsw.nl/item_validate_nl)

Vanaf medio 2025 is dan ook een gegevens-peiling door de GWSW-applicaties actief, daarmee kunnen gemeenten (en Stichting RIONED) de stand van zaken opvragen.
Die peiling levert een beeld van de gegevenskwaliteit, uitgedrukt in volledigheid en actualiteit.

De peiling wordt dagelijks bijgewerkt en gepubliceerd via 

* [apps.gwsw.nl - status monitor]

Aan de basis van de gegevens-peiling voor de Monitor 2028 staan twee queries die gerubriceerd de gemeente-gegevens opvragen.
* Opvragen gegevens van de putten en bouwwerken
* Opvragen gegevens van de leidingen

[apps.gwsw.nl - status monitor]: https://apps.gwsw.nl/item_status_monitor

[Gemengd stelsel]: http://data.gwsw.nl/GemengdStelsel
[Persleidingstelsel]: http://data.gwsw.nl/Persleidingsysteem
[Drukriolering]: http://data.gwsw.nl/Drukriolering

[Rioolput]: https://data.gwsw.nl/Rioolput
[Gemaal]: http://data.gwsw.nl/Gemaal
[Reservoir]: http://data.gwsw.nl/Reservoir
[Uitlaatconstructie]: http://data.gwsw.nl/Uitlaatconstructie
[Inspectieput]: http://data.gwsw.nl/Inspectieput
[Stuwput]: http://data.gwsw.nl/Stuwput
[Overstortput]: http://data.gwsw.nl/Overstortput
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

### Putten en bouwwerken
Van de putten en bouwwerken  worden de subtypes van de volgende GWSW-klassen gegroepeerd (zie groep in de volgende tabel):
* [Rioolput]
* [Gemaal]
* [Reservoir]
* [Uitlaatconstructie]

GWSW-subtypen van putten en bouwwerken die buiten deze groepen vallen zijn niet in de Monitor 2028 betrokken.

Een voorbeeld van het query-resultaat:

Stelsel           | groep      | type           | aantal | jaar
------------------|------------|----------------|--------|-----
[Gemengd stelsel] | [Rioolput] | [Rioolput]     | 1      | 1980
[Gemengd stelsel] | [Rioolput] | [Inspectieput] | 7      | 1970
[Gemengd stelsel] | [Rioolput] | [Stuwput]      | 1      | 1970
[Gemengd stelsel] | [Rioolput] | [Overstortput] | 1      | 1970
[Gemengd stelsel] | [Gemaal]   | [Rioolgemaal]  | 1      | 1980

### Leidingen
Van de leidingen worden de subtypes van de volgende GWSW-klassen gegroepeerd (zie groep in de volgende tabel):
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
* <span class="kwalGreen">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> Gegevens in orde
* <span class="kwalYellow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> Er zijn nog fouten
* <span class="kwalOrange">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> Onvoldoende
* <span class="kwalPurple">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> Fout in analyse

Zoals gezegd meet GWSW Apps dagelijks de kwaliteit voor alle NL-gemeenten en presenteert deze op [apps.gwsw.nl - status monitor].
Die site toont indien gewenst ook de details van de kwaliteitsmeting per gemeente.

Voor de bepaling van de kwaliteit worden de query-resultaten getoetst aan een serie kwaliteitseisen.

Een voorbeeld van deze kwaliteitseisen:

**Putten en bouwwerken**  

id           | mess                                     | weight | eh | <span class="kwalGreen">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | <span class="kwalYellow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | <span class="kwalOrange">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
-------------|------------------------------------------|--------|----|---------|--------|--------
aantal       | Verhouding aantal knooppunten / inwoners | 3      | %  | >5 <100 | >0     | =0     
jaar         | Aanlegjaar aanwezig?                     | 1      | %  | >=5     | >0     | =0     
Inspectieput | Inspectieputten aanwezig?                | 1      | %  | >=85    | >=80   | <80    

**Leidingen**  

id                     | mess                                   | weight | eh | <span class="kwalGreen">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | <span class="kwalYellow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> | <span class="kwalOrange">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
-----------------------|----------------------------------------|--------|----|---------|--------|--------
aantal                 | Verhouding aantal leidingen / inwoners | 3      | %  | >5 <100 | >0     | =0     
jaar                   | Aanlegjaar aanwezig?                   | 1      | %  | >=95    | >=80   | <80    
lengte                 | Gemiddelde leidinglengte               | 1      | m  | >=30    | >=20   | <20   
VrijvervalRioolleiding | Vrijverval rioolleiding aanwezig?      | 1      | %  | >=80    | >=70   | <70    

