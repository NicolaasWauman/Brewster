# Node-red-flow

V1 (oplevering 24/09/2020)
Algemeen process
In de eerste versie is het bedoeling dat aan de hand van de Arduino een temperatuursmeting gebeurd. Manueel kan er een pomp en een verwarmingselement bediend worden.
De Arduino stuurt 2x20char lcd display aan met de temperatuur, status en process stap. Deze info wordt ook reeds naar de Raspberry Pi gestuurd ter visualisatie en logging.

Bediening
Aan de hand van 2 tuimel knoppen is het mogelijk om de pomp en het verwarmingselement manueel te bedienen. De stand van de 2 tuimel knoppen worden uitgelezen door de Arduino zodat de functionaliteit van deze knoppen dynamisch is. Bijvoorbeeld moet het process in stap 0 staan om de knoppen te activeren. De status (knop actief of niet)wordt gevisualiseerd door het blinken van de led op deze knoppen. Als de pomp uitgeschakeld is en de knop is actief is er een korte blink, indien de pomp aan is geschakeld door deze knop is het een lange blink. 

Er zijn ook 3 drukknoppen: manueel/auto, + knop, - knop. Momenteel zijn er 3 dummy stappen voorzien in ons stap programma. In V2 zal de stappenlogica en voorwaarden verhuizen naar de RPI. 