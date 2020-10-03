# Node-red-flow

V1 (oplevering 24/09/2020)
Algemeen process
In de eerste versie is het bedoeling dat aan de hand van de Arduino een temperatuursmeting gebeurd. Manueel kan er een pomp en een verwarmingselement bediend worden.
De Arduino stuurt 2x20char lcd display aan met de temperatuur, status en process stap. Deze info wordt ook reeds naar de Raspberry Pi gestuurd ter visualisatie en logging.

Bediening
Aan de hand van 2 tuimel knoppen is het mogelijk om de pomp en het verwarmingselement manueel te bedienen. De stand van de 2 tuimel knoppen worden uitgelezen door de Arduino zodat de functionaliteit van deze knoppen dynamisch is. Bijvoorbeeld moet het process in stap 0 staan om de knoppen te activeren. De status (knop actief of niet)wordt gevisualiseerd door het blinken van de led op deze knoppen. Als de pomp uitgeschakeld is en de knop is actief is er een korte blink, indien de pomp aan is geschakeld door deze knop is het een lange blink. 

Er zijn ook 3 drukknoppen: manueel/auto, + knop, - knop. Momenteel zijn er 3 dummy stappen voorzien in ons stap programma. In V2 zal de stappenlogica en voorwaarden verhuizen naar de RPI. 

V2
Algemeen process
Arduino blijft de rol houden van uitlezing sensoren en aansturen van uitgangen zoals in V1. De logica van het process (stappendiagram) verhuist naar de RPI. Een algemeen stappendiagram bestaat nu uit vooraf vastgelegde stappen. Deze stappen worden verder aangevuld met info aan de hand van recepten. Deze recepten worden weggeschreven in bestanden (JSON file) en daarin staan tijden en temperaturen beschreven die geladen kunnen worden voor het starten van een batch. Dit is tevens een voorwaarde om een automatisch process te starten. Zonder een recept te laden is het enkel mogelijk om in manuele modus te starten.

In het dashboard van de RPI heb je een paneel met de algemene controle van het proces zelf. Dit omvat:
- Start/Stop brouwen
- Ingave van batch nummer/naam van de run
- Eventueel lijst van aanwezige mensen
- …
We spreken een vast aantal stappen af met bepaalde parameters (pomp aan/ temperaturen die gehaald moeten worden, tijden die verstreken moeten zijn onder bepaalde voorwaarden, …) Als deze structuur wordt aangepast moeten ook de recepten aangepast worden op deze nieuwe structuur.

Op het dashboard, als er geen process via een recept geladen is, wordt er eigenlijk de manuele mode verstaan. In automatische mode kan er geen pomp of verwarmingselement manueel bediend worden. Op eender welk moment in automatische mode kan er overgeschakeld worden van auto naar manueel. Het recept zelf wordt dan niet meer gebruikt. Dit wordt gevisualiseerd in het dashboard en op de knoppen die dit bedienen (auto = lamp autoknop continue, manu = lamp knop blinkend elke seconde). In manuele mode is het de bedoeling om zelf de tijden te beheersen en zelf de processtappen gedurende een manuele tijd te doorlopen tegen een manuele temperatuur.

Bediening
De bediening veranderd niet t.o.v V1, maar de fysieke knoppen zijn ook beschikbaar in het paneel van het dashboard en zijn te bedienen.

V3
Recepten aanmaken via wizard 

Nice to haves:
- Het process vraagt op bepaalde momenten om een steekproef van bijvoorbeeld de brix (sg waarde) van het proces en in te geven  op het dashboard
- Alarmen/meldingen worden via een stem medegedeeld
- Temperatuur regeling en monitoring van het gistproces

Sensors
TankLevel
T1 = meting bovenaan vat
T2  = meting onderaan vat
T3 = ?
T4 = ?
Outputs
Motor
Heating
Temp sensoren:
1=blue=data
2=orange=3-5V
3(earth)=white=gnd