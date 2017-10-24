# Level Of Detail
[terug naar index](/Index.md#graphics)  

Waneer een GameObject verweg staat van de camera kan je nog moeilijk alle details zien van dit object. Wel is zo dat standaard alle polygons wel getekend 
worden. Dit kan je veel performance kosten als er veel objecten zijn die verweg staan van de camera. Om dit te kunnen verkomen kan gewerkt worden met Level of Detail 
(LOD) om objecten verder weg van de camera met minder polygonen te kunnen renderen.  

## Actie Punten
* Leer omgaan met Unity's Level Of Detail systeem  
* Level of Detail models maken voor gebruik in Unity
##  

### Unity LOD 

Unity LOD systeem is volledig te gebruiken via de Editor. Je hebt hier geen code voor nodig. Unity LOD systeem maakt gebruik van 'LODGroups' waarmee in te stellen 
is wanneer een object naar een hoger of lager LOD mesh over zal springen. Met LODGroups kan ingesteld worden wanneer een ander LOD mesh gerenderd moet worden 
dit word veranderd afhankelijk van de vulling van je object ten opzichte van je scherm.

Om een LOD systeem te kunnen bouwen zullen we in eerste instantie verschillende LOD meshes moeten hebben voor hetzelfde object. Hieronder Beginnen we met drie verschillende 
knuppels met een steeds lager polygon aantal.

![LOD_Lod_Compare_Bat](/Afbeeldingen/LOD_Lod_Compare_Bat.png)  

Deze drie objecten zet je in je object hiërarchie onder een leeg object en je noemt deze hoe je het object wil noemen.  

![LOD_Hierarchie](/Afbeeldingen/LOD_Hierarchie.png)  

We voegen aan het parent object een 'LODGroup' toe en voegen onze verschillende objecten toe aan de Renders van de verschillende LOD's.  

![LOD_lod0_inst](/Afbeeldingen/LOD_lod0_instellingen.png)  
![LOD_lod2_inst](/Afbeeldingen/LOD_lod2_instellingen.png)  

Als alles goeg gegaan is kan je nu de camera boven het LOD balkje verschuiven om de verschillende levels van LOD te kunnen zien op je scherm. Duidelijk is dan 
te zien wanneer je object naar een volgende LOD zou gaan en of dit te vroeg of te laat is.

![LOD_lod0_scherm](/Afbeeldingen/LOD_lod0_scherm.png) ![LOD_lod1_scherm](/Afbeeldingen/LOD_lod1_scherm.png)  
![LOD_lod2_scherm](/Afbeeldingen/LOD_lod2_scherm.png) ![LOD_cull_scherm](/Afbeeldingen/LOD_cull_scherm.png)  

Let erop dat de procenten aangeven hoeveel schermvulling het kleinste vierkant om het object heeft en is dus niet afhankelijk van min en max camera distance. 
Zo kan je hierboven zien dat LOD 0 een schermvulling heeft van bijna 100% en dat LOD 2 een schermvulling heeft van minder dan 30%.

#### Sub onderdeel

tekst van het sub onderdeel

https://developer.valvesoftware.com/wiki/LOD_Models



[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LowDetailCamera.md)
---