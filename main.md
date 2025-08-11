# GWSW Revisies

<style>
  .symbolSmall{width:20px;height:20px;margin-right:1em;vertical-align:middle}
  .symbol{width:30px;height:30px;margin-right:1em;vertical-align:middle}
</style>

Stichting RIONED is initiatiefnemer en eigenaar van dit GitHub-project, Eric Oosterom is de verantwoordelijk projectmanager. 

Vragen over deze website en het GWSW kunt u stellen via gwsw@rioned.org. 

# Inleiding

Het initiatief voor dit deelmodel komt voor een belangrijk deel van de GWSW-Opera organisatie. De basis ligt bij een PoC gericht op het ontwikkelen en toetsen van het inmeetproces, 
dus de gegevensuitwisseling tussen landmeter en beheerder.

## Doel en toepassing

Ondersteuning bij revisies en andere metingen van stedelijk water voorzieningen, vooral het efficient en effectief verwerken van inmetingen door de landmeter.

**Revisie**  
De term "revisie" wordt gebruikt voor het inmeten van de objectgegevens na de aanleg (de realisatie van het ontwerp). Dit deelmodel heeft een bredere scoop, 
ook het inmeten van al langer in gebruik zijnde objecten is een toepassing van dit deelmodel. 
Denk dan bijvoorbeeld aan het verbeteren van de bestaande registratie of het actualiseren van gegevens na verzakkingen.

## Leeswijzer

# Projectmodel

Het projectmodel beschrijft globaal het activiteiten-schema van een revisieproject.

**Deelactiviteiten**  
Een revisieproject bestaat uit de deelactiviteiten inmeten knooppunt (put of bouwwerk) en inmeten leiding.
Een deelactiviteit heeft algemene kenmerken zoals meldingen, opmerkingen en de wijze van inwinning.

**Invoer**   
Een knooppunt of leiding met oorspronkelijke kenmerken zoals afmetingen vormt de invoer voor de deelactiviteit. Die gegevens komen uit het beheersysteem of vanuit het ontwerpplan.

**Uitvoer**  
Het ingemeten object wordt als uitvoer van de deelactiviteit beschreven, de ingemeten kenmerken zoals afmetingen en hoogteligging worden - net zoals bij het invoer-object - bij het 
uitvoer-object opgenomen. Waargenomen toestandsgegevens (een soort meting) zoals "meting waterstand" worden als aparte uitvoer bij de deelactiviteit beschreven. 

Hetzelfde fysieke object kan dus (met bijbehorende kenmerken) in twee vormen voorkomen: als invoer (definitie) en/of als uitvoer (resultaat) bij de activiteit.
Volgens het GWSW Datamoel hebben die invoer- en uitvoer-vorm dezelfde objectnaam (rdfs:label) maar een eigen URI, daardoor hebben de bijbehorende kenmerken ook een invoer- en uitvoer-vorm.

<img src="media/Schema Revisieproject.png" style="width:80%;height:80%" />

# Gegevensuitwisseling
Een revisieproject gebruikt gegevens met de projectdefinitie (de beschrijving van de in te meten objecten) en levert gegevens met de projectresultaten (de inmetingen) 
met veelal ook een verschilanalyse en een rapportage daarvan. 

<img src="media/Proces uitwisseling.png" style="width:80%;height:80%" />

## GWSW-OroX formaat
Beheersystemen kunnen veelal omgaan met een GWSW-datasets, ze exporteren of importeren dan een dataset (bestand) conform het GWSW-OroX protocol. 
Zo'n dataset is direct bruikbaar op het GWSW platform, waarmee de gegevens voor allerlei algemene toepassingen beschikbaar komen. 
Bijvoorbeeld kan de inhoud in GIS systemen worden gebruikt. Zie ook https://apps.gwsw.nl.

Ook de gegevens van een revisieproject kunnen via het OroX-protocol worden uitgewisseld, dat is de meest directe vorm van uitwisseling. 
Het complete revisieproject, zowel de definitie als de resultaten past in één dataset.

**Validatie uitwisseling**  
Gebruik voor de validatie van heen- en terug-gegevens ook de tabellen in het volgende hoofdstuk, zie de kolommen "Heen" en "Terug"

Het GWSW-OroX protocol is een speciaal formaat, ingericht op het uitwisselen via het web (linked data) en het kunnen bouwen van ontologiën. 
Een ontologie is een speciale datastructuur waarin de stedelijk water voorzieningen volledig beschreven kunnen worden, dat geldt voor zowel de systemen als de (beheer)processen.

## Tussenvorm CSV of JSON 
Linked data formaten zoals het GWSW-OroX zijn vaak minder bekend bij uitvoerende partijen zoals de landmeter bij inmetingen of de cad-tekenaar bij het ontwerp van systemen.
Om die reden zijn er tussenvormen beschikbaar in bekendere formaten zoals CSV en JSON (minder bekend maar wel eenvoudig van opzet). 
Omzetters van CSV naar JSON en vise versa zijn algemeen beschikbaar.

Via CSV of JSON worden de gegevens uitgewisseld in aparte heen- en terug-bestanden (analoog aan de GWSW-RibX uitwisseling). 
Daardoor is er wel een klein nadeel vanwege enige redundantie (bijvoorbeeld projectgegevens komen dubbel voor).

In deze tussenvorm zijn er vier groepen: Project, Knooppunt, Deksel en Leiding. 
Elk uitwisselgegeven wordt geïdentificeerd door deze groep + de veldcode (zie hierna).  

**CSV**

In het CSV-formaat is het heen- en terug-bestand een zipfile met daarin voor elke groep een apart CSV-bestand. 
De veldcode per groep is de kolomheader in het CSV-bestand.

**Voorbeeld Project.csv uit bestand heen.zip**  
<div class="box"><pre>
Naam;Opdrachtgever;Contractnummer;Omschrijving;Contactpersoon
"Project A";"Opdrachtgever B";"Contract C";"Omschrijving E";"Persoon F"
</pre></div>

**JSON**

In JSON-vorm is elke groep een object binnen het omvattende JSON-object, elk groep-object bevat vervolgens een object-array met daarin objecten met elementnamen conform de veldcode.
In het JSON-formaat is een heen- en terug-bestand een tekstfile met daarin de JSON-string.

**Voorbeeld bestand heen.json**  
<div class="box"><pre>
{
  "Project": [
    {"Naam": "Project A", "Opdrachtgever": "Opdrachtgever B", "Contractnummer": "Contract C", "Omschrijving": "Omschrijving E", "Contactpersoon": "Persoon F"},
  ],
  "Knooppunt": [
  ],
  "Deksel": [
  ],
  "Leiding": [
  ],
}
</pre></div>

In de volgende tabellen staan de uitwisselgegevens per groep, de veldcode identificeert dus het gegeven per groep.

**Vullingsvoorschriften uitwisseling (identiek aan de RibX-definitie):**

De vullingsvoorschriften staan in twee kolommen:
* “Heen”: de veldvulling in een vooraf aangeleverd uitwisselbestand (van de rioleringsbeheerder).
* “Terug”: de veldvulling in een teruggeleverd uitwisselbestand, de resultaten (van de landmeter).

De kolommen “heen” en “terug” gebruiken de volgende codes:

| Code | Voorschrift veldvulling in uitwisselbestand                                 |
|------|-----------------------------------------------------------------------------|
|      | Geen code in kolom “heen”: Niet vooraf invullen                             |
|      | Geen code in kolom “terug”: Niet achteraf invullen (terug zonder wijziging) |
| O    | Optioneel                                                                   |
| A    | Altijd *)                                                                   |

*) Als voor de kolom “heen” geldt dat het gegeven verplicht is (A) en het gegeven ontbreekt in het heen-bestand, dan moet de rioleringsbeheerder met de landmeter 
afspraken maken over de teruglevering. Wanneer het gegeven voor zowel “heen” als “terug” verplicht is (A) en het “heen”-gegeven is fout of ontbreekt (nieuw object, niet vooraf 
ingevuld), dan moet de landmeter dit gegeven – als het bekend is – altijd bij de inmeting corrigeren of aanvullen.

**Link naar datamodel GWSW**

Het GWSW-datamodel beschrijft de gebruikte concepten, de definitie en het waardetype is daarin beschreven.  
Elk concept linkt via een URI naar het GWSW-datamodel (de deelmodellen onder http://data.gwsw.nl/totaal of http://data.gwsw.nl/revisies).


**Gegevens Project**  

| Veldcode       | Omschrijving         | Waardetype (in RDF-termen)                     | Heen | Terug | Opmerking                                  |
|----------------|----------------------|------------------------------------------------|------|-------|--------------------------------------------|
| Naam           | Naam project         | rdfs:label bij [Revisieproject]                | A    |       | in Opera Project_Id                        |
| Opdrachtgever  | Opdrachtgever        | rdfs:label bij [Opdrachtgever]                 | A    |       |                                            |
| Contractnummer | Contractnummer       | gwsw:hasValue [ProjectreferentieOpdrachtnemer] | A    |       |                                            |
| Omschrijving   | Omschrijving project | rdfs:comment bij [Revisieproject]              | A    |       | in Opera Projectomschrijving               |
| Contactpersoon | Contactpersoon       | rdfs:label bij [Contactpersoon]                | A    |       | in Opera ProjectAdministratorOpdrachtgever |

[Revisieproject]: http://data.gwsw.nl/revisies/Revisieproject
[Opdrachtgever]: http://data.gwsw.nl/totaal/Opdrachtgever
[ProjectreferentieOpdrachtnemer]: http://data.gwsw.nl/totaal/ProjectreferentieOpdrachtnemer
[Contactpersoon]: http://data.gwsw.nl/revisies/Contactpersoon

**Gegevens Knooppunt** (Put of Bouwwerk)  

| Veldcode             | Omschrijving               | Waardetype (in RDF-termen)                      | Heen | Terug | Opmerking                    |
|----------------------|----------------------------|-------------------------------------------------|------|-------|------------------------------|
| Naam                 | Naam put of bouwwerk       | rdfs:label bij [Put] of [Bouwwerk]              | A    | A     | in Opera Knooppuntreferentie |
| Type                 | Type put of bouwwerk       | rdf:type [Put] of [Bouwwerk]                    | O    | A     | in Opera SoortPut            |
| NaamStelsel          | Naam stelsel               | rdfs:label bij [Stelsel]                        | A    | A     |                              |
| TypeStelsel          | Type stelsel               | rdf:type [Stelsel]                              | O    | O     |                              |
| WijzeVanInwinning    | Wijze van inwinning        | gwsw:hasReference [WijzeVanInwinningColl]       |      | A     |                              |
| DatumInwinning       | Datum inwinning            | gwsw:hasValue [DatumInwinning]                  |      | A     |                              |
| Vorm                 | Vorm put of bouwwerk       | gwsw:hasReference [VormPutColl]                 | O    | A     | in Opera VormPut             |
| Breedte              | Breedte put of bouwwerk    | gwsw:hasValue [BreedtePut] of [BreedteBouwwerk] | O    | A     | in Opera BreedtePut          |
| Lengte               | Lengte put of bouwwerk     | gwsw:hasValue [LengtePut] of [LengteBouwwerk]   | O    | A     | in Opera LengtePut           |
| Materiaal            | Materiaal put of bouwwerk  | gwsw:hasReference [MateriaalPutColl]            | O    | A     | in Opera MateriaalPut        |
| Bodemprofiel         | Bodemprofiel               | gwsw:hasReference [BodemprofielColl]            | O    | A     | Vanaf GWSW 1.6.1             |
| X                    | X coördinaat               | gwsw:hasValue [Punt]                            | A    | A     | in Opera X_coordinaat        |
| Y                    | Y coördinaat               | gwsw:hasValue [Punt]                            | A    | A     | in Opera Y_coordinaat        |
| Z                    | Z coördinaat               | gwsw:hasValue [Punt]                            | O    | O     | in Opera Z_coordinaat        |
| Hoogte               | Hoogte put of bouwwerk     | gwsw:hasValue [HoogtePut] of [HoogteBouwwerk]   | O    | A     |                              |
| StatusFunctioneren   | Status functioneren        | gwsw:hasReference [StatusFunctionerenColl]      | O    | A     |                              |
| Constructieonderdeel | Bevat constructieonderdeel | rdf:type [Constructieonderdeel]                 | O    | A     |                              |
| Drempelniveau        | Drempelniveau              | gwsw:hasValue [Drempelniveau]                   | O    | A     |                              |
| HoogteStellaag       | Hoogte stellaag            | gwsw:hasValue [HoogteStellaag]                  | O    | A     | Vanaf GWSW 1.6.1             |
| Waterstand           | Meting waterstand          | gwsw:hasValue [MetingWaterstand]                |      | A     |                              |
| Fotoreferentie       | Fotoreferentie             | rdfs:seeAlso bij [Put] of [Bouwwerk]            |      | O     |                              |
| Melding              | Melding meting knooppunt   | gwsw:hasReference [MeldingMetingKnooppuntColl]  |      | O     | in Opera MeldingPut          |
| Opmerking            | Opmerking                  | gwsw:hasValue [Opmerking]                       |      | O     | in Opera rdfs:comment        |

[Put]: http://data.gwsw.nl/totaal/Put
[Bouwwerk]: http://data.gwsw.nl/totaal/Bouwwerk
[VormPutColl]: http://data.gwsw.nl/totaal/VormPutColl
[BreedtePut]: http://data.gwsw.nl/totaal/BreedtePut
[BreedteBouwwerk]: http://data.gwsw.nl/totaal/BreedteBouwwerk
[LengtePut]: http://data.gwsw.nl/totaal/LengtePut
[LengteBouwwerk]: http://data.gwsw.nl/totaal/LengteBouwwerk
[MateriaalPutColl]: http://data.gwsw.nl/totaal/MateriaalPutColl
[BodemprofielColl]: http://data.gwsw.nl/totaal/BodemprofielColl
[Punt]: http://data.gwsw.nl/totaal/Punt
[HoogtePut]: http://data.gwsw.nl/totaal/HoogtePut
[HoogteBouwwerk]: http://data.gwsw.nl/totaal/HoogteBouwwerk
[StatusFunctionerenColl]: http://data.gwsw.nl/totaal/StatusFunctionerenColl
[Stelsel]: http://data.gwsw.nl/totaal/Stelsel
[Constructieonderdeel]: http://data.gwsw.nl/totaal/Constructieonderdeel
[Drempelniveau]: http://data.gwsw.nl/totaal/Drempelniveau
[MeldingMetingKnooppuntColl]: http://data.gwsw.nl/revisies/MeldingMetingKnooppuntColl
[WijzeVanInwinningColl]: http://data.gwsw.nl/totaal/WijzeVanInwinningColl
[DatumInwinning]: http://data.gwsw.nl/totaal/DatumInwinning
[MetingWaterstand]: http://data.gwsw.nl/revisies/MetingWaterstand
[HoogteStellaag]: http://data.gwsw.nl/totaal/HoogteStellaag
[Opmerking]: http://data.gwsw.nl/totaal/Opmerking

**Gegevens Deksel**  

| Veldcode  | Omschrijving          | Waardetype (in RDF-termen)                  | Heen | Terug | Opmerking                    |
|-----------|-----------------------|---------------------------------------------|------|-------|------------------------------|
| Naam      | Naam put of bouwwerk  | rdfs:label bij [Put] of [Bouwwerk]          | A    | A     | in Opera Knooppuntreferentie |
| Type      | Type deksel           | rdf:type [Afdekking]                        | O    | A     | in Opera SoortDeksel         |
| Vorm      | Vorm deksel           | gwsw:hasReference [VormDekselColl]          | O    | A     | in Opera VormDeksel          |
| Lengte    | Lengte deksel         | gwsw:hasValue [LengteDeksel]                | O    | A     | in Opera LengteDeksel        |
| Breedte   | Breedte deksel        | gwsw:hasValue [BreedteDeksel]               | O    | A     | in Opera BreedteDeksel       |
| Materiaal | Materiaal deksel      | gwsw:hasReference [MateriaalDekselColl]     | O    | A     | in Opera MateriaalDeksel     |
| Melding   | Melding meting deksel | gwsw:hasReference [MeldingMetingDekselColl] |      | O     | in Opera MeldingDeksel       |

[Afdekking]: http://data.gwsw.nl/totaal/Afdekking
[VormDekselColl]: http://data.gwsw.nl/totaal/VormDekselColl
[LengteDeksel]: http://data.gwsw.nl/totaal/LengteDeksel
[BreedteDeksel]: http://data.gwsw.nl/totaal/BreedteDeksel
[MateriaalDekselColl]: http://data.gwsw.nl/totaal/MateriaalDekselColl
[MeldingMetingDekselColl]: http://data.gwsw.nl/revisies/MeldingMetingDekselColl

**Gegevens Leiding**  

| Veldcode           | Omschrijving            | Waardetype (in RDF-termen)                   | Heen | Terug | Opmerking                     |
|--------------------|-------------------------|----------------------------------------------|------|-------|-------------------------------|
| Naam               | Naam leiding            | rdfs:label bij [Leiding]                     | A    | A     | in Opera Leiding_id           |
| Type               | Type leiding            | rdf:type [Leiding]                           | O    | A     | in Opera Leidingtype          |
| NaamStelsel        | Naam stelsel            | rdfs:label bij [Stelsel]                     | A    | A     |                               |
| TypeStelsel        | Type stelsel            | rdf:type [Stelsel]                           | O    | O     |                               |
| WijzeVanInwinning  | Wijze van inwinning     | gwsw:hasReference [WijzeVanInwinningColl]    |      | A     |                               |
| DatumInwinning     | Datum inwinning         | gwsw:hasValue [DatumInwinning]               |      | A     |                               |
| NaamKnooppuntBegin | Naam knooppunt begin    | rdfs:label bij [Put] of [Bouwwerk]           | A    | A     | in Opera Knooppuntreferentie1 |
| NaamKnooppuntEind  | Naam knooppunt eind     | rdfs:label bij [Put] of [Bouwwerk]           | A    | A     | in Opera Knooppuntreferentie2 |
| BobKnooppuntBegin  | Bob bij knooppunt begin | gwsw:hasValue [BobBeginpuntLeiding]          | O    | A     | in Opera BobBeginpuntLeiding  |
| BobKnooppuntEind   | Bob bij knooppunt eind  | gwsw:hasValue [BobEindpuntLeiding]           | O    | A     | in Opera BobEindpuntLeiding   |
| BbbKnooppuntBegin  | Bbb bij knooppunt begin | gwsw:hasValue [BbbBeginpuntLeiding]          |      | A     | in Opera BbbBeginpuntLeiding  |
| BbbKnooppuntEind   | Bbb bij knooppunt eind  | gwsw:hasValue [BbbEindpuntLeiding]           |      | A     | in Opera BbbEindpuntLeiding   |
| StatusFunctioneren | Status functioneren     | gwsw:hasReference [StatusFunctionerenColl]   | O    | A     |                               |
| Vorm               | Vorm leiding            | gwsw:hasReference [VormLeidingColl]          | O    | A     | in Opera VormLeiding          |
| Hoogte             | Hoogte leiding          | gwsw:hasValue [HoogteLeiding]                | O    | A     | in Opera HoogteLeiding        |
| Breedte            | Breedte leiding         | gwsw:hasValue [BreedteLeiding]               | O    | A     | in Opera BreedteLeiding       |
| Materiaal          | Materiaal leiding       | gwsw:hasReference [MateriaalLeidingColl]     | O    | A     | in Opera MateriaalLeiding     |
| Fotoreferentie     | Fotoreferentie          | rdfs:seeAlso bij [Put] of [Bouwwerk]         |      | O     |                               |
| Melding            | Melding meting leiding  | gwsw:hasReference [MeldingMetingLeidingColl] |      | O     | in Opera MeldingLeiding       |
| Opmerking          | Opmerking               | gwsw:hasValue [Opmerking]                    |      | O     | in Opera rdfs:comment         |

[Leiding]: http://data.gwsw.nl/totaal/Leiding
[BobBeginpuntLeiding]: http://data.gwsw.nl/totaal/BobBeginpuntLeiding
[BobEindpuntLeiding]: http://data.gwsw.nl/totaal/BobEindpuntLeiding
[BbbBeginpuntLeiding]: http://data.gwsw.nl/revisies/BbbBeginpuntLeiding
[BbbEindpuntLeiding]: http://data.gwsw.nl/revisies/BbbEindpuntLeiding
[VormLeidingColl]: http://data.gwsw.nl/totaal/VormLeidingColl
[HoogteLeiding]: http://data.gwsw.nl/totaal/HoogteLeiding
[BreedteLeiding]: http://data.gwsw.nl/totaal/BreedteLeiding
[MateriaalLeidingColl]: http://data.gwsw.nl/totaal/MateriaalLeidingColl
[MeldingMetingLeidingColl]: http://data.gwsw.nl/revisies/MeldingMetingLeidingColl

# Datamodel

## Nieuwe GWSW-concepten

Veel URI's staan al in het GWSW datamodel, voor het deelmodel Revisies zijn ook een aantal nieuwe concepten uitgewerkt (in de hoofdstukken hiervoor staan al enkele van die concepten).

Een overzicht van de nieuwe concepten (exclusief in concept-deelmodel GWSW-Revisies 1.6.1):

| URI                          | Naam                              | Definitie                                                                                | 
|------------------------------|-----------------------------------|------------------------------------------------------------------------------------------|
| [Revisieproject]             | Revisieproject                    |                                                                                          | 
| [InmetenKnooppunt]           | Inmeten knooppunt                 | Inmeten van een put of bouwwerk met eventuele deksel (deelactiviteit van Revisieproject) | 
| [InmetenLeiding]             | Inmeten leiding                   | Inmeten van een leiding (deelactiviteit van Revisieproject)                              | 
| [MetingWaterstand]           | Meting waterstand                 | De gemeten waterstand tov de constructiebodem                                            | 
| [MeldingMetingKnooppuntColl] | Melding bij meting knooppunt      | Voorgedefinieerde meldingen bij de meting van een put of bouwwerk                        |
| [MeldingMetingDekselColl]    | Melding bij meting deksel         | Voorgedefinieerde meldingen bij de meting van een deksel                                 |  
| [MeldingMetingLeidingColl]   | Melding bij meting leiding        | Voorgedefinieerde meldingen bij de meting van een leiding                                | 
| [BbbBeginpuntLeiding]        | Binnenbovenkant beginpunt leiding | Het niveau van de binnenbovenkant bij het topologische beginpunt                         |
| [BbbEindpuntLeiding]         | Binnenbovenkant eindpunt leiding  | Het niveau van de binnenbovenkant bij het topologische eindpunt                          | 

[InmetenKnooppunt]: http://data.gwsw.nl/revisies/InmetenKnooppunt
[InmetenLeiding]: http://data.gwsw.nl/revisies/InmetenLeiding

## Datamodel Revisies in RDF

Hieronder staat het eerste concept model met daarin alleen de toegevoegde revisie-concepten (in de uitgewerkte versies wordt de prefix rev: vervangen door gwsw: ).  

De uitwerking van het complete deelmodel GWSW-Revisies staat onder https://data.gwsw.nl/Revisies.

<div class="example"><div class="example-title marker">Datamodel: Revisieproject</div><pre>

rev:Revisieproject rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Project ;
  rdfs:label "Revisieproject";
  skos:definition "Revisieproject" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenKnooppunt ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenLeiding (min=0)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenLeiding ;
    owl:onProperty gwsw:hasPart ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:InmetenKnooppunt rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meten ;
  rdfs:label "Inmeten knooppunt" ;
  skos:definition "Landmeetkundige inmeting van een put of bouwwerk" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit Revisieproject (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:Revisieproject ;
    owl:onProperty gwsw:isPartOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk WijzeVanInwinning (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:WijzeVanInwinning ;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk DatumInwinning (exact=1)
    rdf:type owl:Restriction;
    owl:onClass gwsw:DatumInwinning;
    owl:onProperty gwsw:hasAspect;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Put (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Bouwwerk (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Bouwwerk ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Put (projectresultaat) (max=1, kan ook Bouwwerk zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:hasOutput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Bouwwerk (projectresultaat) (max=1, kan ook Put zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Bouwwerk ;
    owl:onProperty gwsw:hasOutput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingKnooppunt (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingKnooppunt ;
    owl:onProperty gwsw:hasAspect ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingDeksel (min=0, er kunnen meerdere (niet geïdentificeerde) deksels zijn)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingDeksel ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk Opmerking (min=0, er kunnen er meerdere zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Opmerking ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:InmetenLeiding rdf:type owl:Class ;
  rdfs:subClassOf gwsw:Meten ;
  rdfs:label "Inmeten leiding" ;
  skos:definition "Landmeetkundige inmeting van een leiding" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit Revisieproject (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:Revisieproject ;
    owl:onProperty gwsw:isPartOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk WijzeVanInwinning (exact=1)
    rdf:type owl:Restriction;
    owl:onClass gwsw:WijzeVanInwinning;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk DatumInwinning (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:DatumInwinning ;
    owl:onProperty gwsw:hasAspect ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Leiding (projectdefinitie) (max=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Leiding ;
    owl:onProperty gwsw:hasInput ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op fysiek object Leiding (projectresultaat) (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Leiding ;
    owl:onProperty gwsw:hasOutput ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk MeldingMetingLeiding (max=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:MeldingMetingLeiding ;
    owl:onProperty gwsw:hasAspect ;
    owl:maxQualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op kenmerk Opmerking (min=0, er kunnen er meerdere zijn)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Opmerking ;
    owl:onProperty gwsw:hasAspect ;
    owl:minQualifiedCardinality "0"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingMetingKnooppunt rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting knooppunt";
  skos:definition "Melding bij meting van put of bouwwerk";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingMetingDeksel rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting deksel" ;
  skos:definition "Melding bij meting van putdeksel" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetengKnooppunt ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MeldingMetingLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Melding meting leiding" ;
  skos:definition "Melding bij meting van leiding" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass rev:InmetenLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:MetingWaterstand rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "Gemeten waterstand bij revisie-object" ;
  skos:definition "Gemeten waterstand bij de meting van een object, de hoogte tov de bodem";
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op activiteit InmetenKnooppunt (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:Put ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:BbbBeginpuntLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "B.b.b. beginpunt leiding" ;
  skos:definition "Niveau binnenbovenkant buis ter plaatse van het beginpunt" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op topologisch element BeginpuntLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:BeginpuntLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
rev:BbbEindpuntLeiding rdf:type owl:Class ; 
  rdfs:subClassOf gwsw:Kenmerk ;
  rdfs:label "B.b.b. eindpunt leiding" ;
  skos:definition "Niveau binnenbovenkant buis ter plaatse van het eindpunt" ;
  rdfs:subClassOf \[ \# Kardinaliteits-restricie op topologisch element EinduntLeiding (exact=1)
    rdf:type owl:Restriction ;
    owl:onClass gwsw:EindpuntLeiding ;
    owl:onProperty gwsw:isAspectOf ;
    owl:qualifiedCardinality "1"^^xsd:nonNegativeInteger ;
  ] ;
  skos:scopeNote rev:Cof_REV; \# Nieuw concept in deelmodel GWSW-Revisies
.
</pre> </div>

## Projectmodel revisies in RDF (dataset)

Als we de meetgegevens combineren met het eerder beschreven projectmodel kan een GWSW-dataset worden opgebouwd.
Zo'n GWSW-dataset omvat de uitwisseling binnen het volledige project, dus zowel de gegevens van de heen- als van de terug-levering.  

Het ziet er dan als volgt uit (in één GWSW-dataset):

<div class="example-dataset"><div class="example-title marker">Dataset: Voorbeeld revisieproject</div><pre>

\# ex: - prefix met de individuen, de objecten in de projectdefintie en in het terrein
\# gwsw: - bestaande gwsw-concepten
\# rev: - concepten in deelmodel GWSW-Revisies
\# rdf: / rdfs: - generieke RDF-concepten

{ex:01} \# Revisieproject
  rdfs:label {Project.Naam} ;
  rdf:type rev:Revisieproject ;
  gwsw:isOutputOf \[ rdf:type gwsw:Opdrachtgever ; rdfs:label {Project.Opdrachtgever} ; ] ;
  gwsw:hasAspect \[ rdf:type rev:Contractnummer ; gwsw:hasValue {Project.Contractnummer} ; ] ;
  gwsw:isOutputOf \[ rdf:type gwsw:Contactpersoon ; rdfs:label {Project.Contactpersoon} ; ] ;
  rdfs:comment {Project.Omschrijving} ;
.
{ex:10} \# Inmeten knooppunt - activiteit
  gwsw:isPartOf {ex:01} ; 
  rdf:type rev:InmetenKnooppunt ;
.
{ex:10} \# Inmeten knooppunt - projectdefinitie (heen)
  gwsw:hasInput {ex:11i} ;
.
{ex:10} \# Inmeten knooppunt - resultaat (terug)
  gwsw:hasOutput {ex:11o} ; \# Gebruik een andere URI dan ex:11i, ook bij hetzelfde knooppunt (houdt dezelfde naam)
  gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {InmetenKnooppunt.WijzeVanInwinning}; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {InmetenKnooppunt.DatumInwinning} ; ] ;
  rdfs:seeAlso {InmetenKnooppunt.FotoReferentie} ;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingKnooppunt ; gwsw:hasValue {Knooppunt.Melding} ; ] ;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingDeksel ; gwsw:hasValue {Deksel.Melding} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue {InmetenKnooppunt.Opmerking} ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug
  rdf:type {Knooppunt.Type} ; /# Ga hier uit van supertype gwsw:Put 
  rdfs:label {Knooppunt.Naam} ;
  gwsw:hasAspect \[ rdf:type gwsw:VormPut ; gwsw:hasReference {Knooppunt.Vorm} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedtePut ; gwsw:hasValue {Knooppunt.Breedte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:LengtePut ; gwsw:hasValue {Knooppunt.Lengte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalPut ; gwsw:hasReference {Knooppunt.Materiaal} ; ] ;
  gwsw:hasPart \[ rdf:type gwsw:Stroomprofiel; gwsw:hasAspect \[ rdf:type gwsw:VormStroomprofiel ; gwsw:hasReference {Knooppunt.Stroomprofiel} ; ] ; ] ;
  gwsw:hasPart \[ rdf:type gwsw:Stellaag; gwsw:hasAspect \[ rdf:type gwsw:HoogteStellaag ; gwsw:hasValue {Knooppunt.Stellaag} ; ] ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:HoogtePut ; gwsw:hasValue {Knooppunt.Hoogte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Knooppunt.StatusFunctioneren} ; ] ;
  gwsw:isPartOf \[ rdf:type {Knooppunt.TypeStelsel}; ] ;
  gwsw:hasPart \[ rdf:type {Knooppunt.Constructieonderdeel}; gwsw:hasAspect \[ rdf:type gwsw:Drempelniveau ; gwsw:hasValue {Knooppunt.Drempelniveau} ; ] ; ] ;
.
{ex:11i/ex:11o} \# Knooppunt heen en terug: de verbinding
  gwsw:hasAspect {ex:12i/ex:12o} ;
.
{ex:12i/ex:12o} 
  rdf:type gwsw:Putorientatie ;
  gwsw:hasAspect \[ rdf:type gwsw:Punt ; gwsw:hasValue "gml:Point {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}" ; ] ;
.
{ex:11o} \# Knooppunt terug
  gwsw:hasAspect \[ rdf:type rev:MetingWaterstand ; gwsw:hasValue {Knooppunt.MetingWaterstand} ; ] ;
.
{ex:13i/ex:13o} \# Deksel heen en terug 
  rdf:type {Deksel.Type} ;
  gwsw:isPartOf {ex:11i/i11o} ; # Afleiden uit {Deksel.NaamKnooppunt}
  gwsw:hasAspect \[ rdf:type gwsw:VormDeksel ; gwsw:hasReference {Deksel.Vorm} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedteDeksel ; gwsw:hasValue {Deksel.Breedte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:LengteDeksel ; gwsw:hasValue {Deksel.Lengte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalDeksel ; gwsw:hasReference {Deksel.Materiaal} ; ] ;
.
{ex:20} \# Inmeten Leiding - activiteit
  gwsw:isPartOf {ex:01} ; 
  rdf:type rev:InmetenLeiding ;
.
{ex:20} \# Inmeten Leiding - projectdefinitie (heen)
  gwsw:hasInput {ex:21i} ;
.
{ex:20} \# InmetenLeiding: - resultaat (terug)
  gwsw:hasOutput {ex:21o} ; \# Gebruik een andere URI dan ex:21i, ook bij dezelfde leiding (houdt dezelfde naam)
  gwsw:hasAspect \[ rdf:type gwsw:WijzeVanInwinning ; gwsw:hasReference {Leiding.WijzeVanInwinning}; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:DatumInwinning ; gwsw:hasValue {Leiding.DatumInwinning} ; ] ;
  gwsw:hasAspect \[ rdf:type rev:MeldingMetingLeiding ; gwsw:hasValue {Leiding.Melding} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:Opmerking ; gwsw:hasValue {Leiding.Opmerking} ; ] ;
  rdfs:seeAlso {Leiding.FotoReferentie} ;
.
{ex:21i/ex:21o} \# Leiding heen en terug
  rdf:type {Leiding.Type} ;
  rdfs:label {Leiding.Naam} ;
  gwsw:hasAspect \[ rdf:type gwsw:StatusFunctioneren ; gwsw:hasReference {Leiding.StatusFunctioneren} ; ] ;
  gwsw:isPartOf \[ rdf:type {Leiding.TypeStelsel}; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:VormLeiding ; gwsw:hasReference {Leiding.Vorm} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:HoogteLeiding ; gwsw:hasValue {Leiding.Hoogte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:BreedteLeiding ; gwsw:hasValue {Leiding.Breedte} ; ] ;
  gwsw:hasAspect \[ rdf:type gwsw:MateriaalLeiding ; gwsw:hasReference {Leiding.Materiaal} ; ] ;
.
{ex:21i/ex:21o} \# Leiding heen en terug: de verbinding
  gwsw:hasAspect {ex:22} ;
.
{ex:22} 
  rdf:type gwsw:Leidingorientatie ; \# Afleiden uit {Leiding.KnooppuntBegin} en {Leiding.KnooppuntEind} 
  gwsw:hasAspect \[ rdf:type gwsw:Lijn ; gwsw:hasValue "gml:LineString {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}, {Knooppunt.X} {Knooppunt.Y} {Knooppunt.Z}" ; ] ;
  gwsw:hasPart {ex:23} ;
  gwsw:hasPart {ex:24} ;
.
{ex:23} \# Leiding heen en terug: beginpunt
  rdf:type gwsw:BeginpuntLeiding ; 
  gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntBegin}
  gwsw:hasAspect \[ rdf:type gwsw:BobBeginpuntLeiding ; gwsw:hasValue {Leiding.BobKnooppuntBegin} ; ] ;
.
{ex:24} \# Leiding heen en terug: eindpunt 
  rdf:type gwsw:EindpuntLeiding ; 
  gwsw:hasConnection {ex:12} ; \# Afleiden uit {Leiding.KnooppuntEind} {ex:12} is natuurlijk een andere put
  gwsw:hasAspect \[ rdf:type gwsw:BobEindpuntLeiding ; gwsw:hasValue {Leiding.BobKnooppuntEind} ; ] ;
.
{ex:241} \# Beginpunt terug
  gwsw:hasAspect \[ rdf:type rev:BbbBeginpuntLeiding ; gwsw:hasValue {Leiding.BbbKnooppuntBegin} ; ] ;
.
{ex:24o} \# Eindpunt terug
  gwsw:hasAspect \[ rdf:type rev:BbbEindpuntLeiding ; gwsw:hasValue {Leiding.BbbKnooppuntEind} ; ] ;
.
 </pre> </div>



