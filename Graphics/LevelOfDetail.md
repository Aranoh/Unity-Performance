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

### Maken LOD Models

Het maken van een low poly model kan vaak automatish gedaan worden. Meeste 3D programma's hebben hier functionaliteit voor. Het nadeel van automatish genereren 
van low poly models is dat je hier weinig controle over hebt. Models kunnen soms raar eruit komen bij gebruik van zo'n functionaliteit. Let altijd op dat de 
modellen waarbij je automatishe verkleining van poly count gebruikt er aan het einde ook nog goed en bruikbaar uitzien.

Voor je begint met het verminderen van de polygonen denk erover na wat je vanaf een afstand niet meer zou kunnen zien. Vaak kunnen heel veel polygonen gewoon 
weg gehaald worden. Denk bijvoorbeeld aan een knoop van een jas of een los hangend kabeltje van een apparaat.

Op bijvoorbeeld youtube zijn veel video's te vinden over hoe poly count verminderd kan worden.

Wat voorbeelden:  
[Maya tutorial](https://www.youtube.com/watch?v=-Ztme74jJzE)  
[Blender tutorial](https://www.youtube.com/watch?v=ttU6Gz1W0Xw)  
[3ds Max tutorial](https://www.youtube.com/watch?v=tpeGsGCLw3E)  

### Low Detail Camera

Een interessant alternatief van LOD is het gebruiken van een 2e 'Low Detail Camera'. Door het combineren van twee camera's een high detail voor objecten 
dichtbij de camera en een voor objecten ver weg. Door in te stellen welke objecten wel en niet gezien worden door de 2e camera en door de resolutie van 
deze camera te verkleinen kan een grotere vieuw distance bereikt worden zonder hierdoor teveel fps te hoeven verliezen.  

De twee camera's in Unity zullen gebruik maken van layers om te bepalen welke objecten niet in het 2e camera beeld tevoorschijn komen. zo kan je 
instellen dat bijvoorbeeld plantjes en kleine stukjes gras niet te zien zijn op de 2e camera aangezien je ze toch bijna niet ziet. Hierdoor hoef 
je deze objecten niet te renderen wat weer zorgd voor meer framerate.

![Visualisatie Low Detail Camera](/Afbeeldingen/PS_MinMaxCurve_small.png)  

Door gebruik van dit systeem hoeven geen LOD modellen gemaakt te worden. Dit is voor games op mobiel extra interessant aangezien je op mobiel 
vaak voor je originele modellen ook al weinig polygonen gebruikt en een LOD model weinig toevoegd. 

Voor meer informatie over deze low detail camera, inclusief een 'Pseudo-coded breakdown' van hoe 'Little Chicken Game Company' dit systeem geïmplementeerd heeft:
[Source: KLM Jets Low Detail Camera](https://www.gamasutra.com/blogs/TomasSala/20150929/254839/KLM_Jets_Doubling_viewingdistance_without_LODing_or_performancedrop.php)  

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LowDetailCamera.md)
