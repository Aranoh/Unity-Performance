# Draw Calls & Batching
[terug naar index](/Index.md#unity-settings)  

Het tekenen van een object op het scherm gaat via 'Draw Calls'. Draw calls zijn te verglijken met een schilder die nieuwe (en andere) verf op zijn 
kwast doet om daarna weer iets moois te schilderen. Zo is in Unity elk object met een nieuwe material weer een nieuwe draw call om zo min mogelijk 
draw calls te krijgen in je scene moeten we weten waar extra draw calls vandaan komen.  

Voor next gen PC games is het vaak niet erg om duizenden draw calls te hebben maar op mobile is het wel vrij belangerijk om zo min mogelijk draw 
calls te hebben. Er word veel aangeraden om niet boven de 50 draw calls te komen met je game om zeker te weten dat je ook low en devices kan ondersteunen.  

## Actie Punten
* Weet waar draw calls vandaan komen
* Gebruik static batching om het statishe deel van je scene effectief te kunnen tekenen
* Gebruik goede instellingen voor dynamishe objecten zodat dynamic batching zijn werk kan doen
##  

### Automatic batching 

Om een beter beeld te krijgen van hoe draw calls verlaagd kunnen worden moeten we weten wanneer Unity niet in staat is om 'batching' toe te passen. 
Batching zal automatish gebeuren zolang Unity objecten tegen komt die met dezelfde 'kwast' getekend kunnen worden. Dit proces heet 'Dynamic batching'. 
Dynamic batching zal automatish gebeuren zonder dat je hier iets voor hoeft te doen. Wel moeten objecten aan bepaalde criterea voldoen om gebatched 
te mogen worden.

* Een object mag niet meer dan 900 vertices anders zal het niet mee genomen worden in batching.  
Dynamic batching is niet gratis. Om ervoor te zorgend dat het geen framerate gaat kosten is er een limiet op het aantal vertices. Deze limit zal 
veranderen met het gebruik van complexe shaders. Bij gebruik van Vertex positie, Normal en UV map bijvoorbeeld zit de limiet op 300.

* Game objecten worden niet gebatched als ze spiegelen over te transform.  
Dit wil zeggen dat objecten met een scale van -1 niet gebatched kunnen worden met objecten met een scale van +1.
 
* Batching kan niet gebeuren wanneer verschillende materials gebruikt worden.  
Elke nieuwe material zal op zijn minst een extra draw call maken. Objecten met dezelfde material kunnen wel gebatched worden.

* Alleen objecten met dezelfde gebakken light map kunnen gebatched worden.  
Wanneer verschillende objecten niet presies dezelfde lightmap locatie gebruiken kunnen deze niet gebatched worden.

* Multi pass shaders worden niet gebatched.  
Shaders die gebruik maken van meerdere passes om bijvoorbeeld licht inval te renderen worden niet mee genomen in dynamic batching.

Buiten 'Dynamic batching' kan Unity nog een tweede automatishe techniek toepassen. Deze techniek word gebruikt op objecten die gemarkeerd 
zijn als 'static'. Deze techniek heet dan ook 'Static batching'. Static batching is efficiënter dan dynamic batching maar gebruikt wel iets 
meer memory. Static batching gebeurd zolang verschillende objecten dezelfde material gebruiken.

### Manual batching

Buiten Unity's eigen technieken om draw calls te batchen kunnen wij zelf ook wat doen om objecten te batchen. Dit kan met scripts gedaan 
worden maar ook kunnen artists hier op inspelen met het maken van textures en modellen.  

#### Scripting batching

Wat veel gedaan word is gebruik maken van een zogenoemde 'mesh and texture combiner'. Deze kan zelf geschreven worden, maar aan te raden is 
om een van de vele gratis implementaties van dit systeem te gebruiken. Met dergelijke scripts kunnen verschillende objecten met dezelfde shaders 
aan elkaar geknipt worden tot een object. Unity hoeft dan zelf niet meer na te denken over batching waardoor weer wat extra framerate behaald 
kan worden.  

Let op dat deze techniek niet altijd even handig kan zij. Zo kan bijvoorbeeld culling niet meer toegepast worden wanneer alle meshes aan elkaar 
geplakt zijn en ook kunnen aan elkaar geplakte objecten niet afzonderlijk bewegen of verwijderd worden.

Handige tool voor combineren mesh en textures:  
[MaTC door Tatsuya Sato](https://bitbucket.org/ciitt/mesh-and-texture-combiner)  

#### Batching in 3D modelleren

De techniek die hierboven beschreven staat kan ook door de artist gemaakt worden. Over het algemeen maak je losse objecten om ze dan in Unity weer 
te kunnen combineren tot een stad of andere omgeving. Wat bij het 3D modelleren gedaan kan worden is verschillende modellen van dezelfde texture 
atlas gebruik te laten maken. Door dezelfde texture te gebruiken voor verschillende modellen kan Unity sneller en efficiënter batching toepassen 
op deze objecten. Ook zal het memory verbruik van verschillende objecten met dezelfde texture atlas een stuk lager liggen.  

### Frame debugger

Het kan af en toe niet meteen duidelijk zijn waarom bepaalde objecten niet gebatched kunnen worden. In deze gevallen kunnen we gebruik maken van 
Unity's frame debugger. Frame debugger kan per frame alle draw calls los laten zien. Unity bij veel draw calls ook aangeven waarom deze draw call 
niet samengevoegd kon worden aan de vorrige.  

![Draw_Calls_FrameDebuggerA](/Afbeeldingen/Draw_Calls_FrameDebuggerA.png)  
![Draw_Calls_FrameDebuggerB](/Afbeeldingen/Draw_Calls_FrameDebuggerB.png)  
![Draw_Calls_FrameDebuggerC](/Afbeeldingen/Draw_Calls_FrameDebuggerC.png)  

Door de lijst van draw calls langzaam af te werken kan je draw calls vaak al genoeg verminderen tot je op een gewenst aantal zit. Ga hierna pas 
kijken naar niet automatishe batching methode's.   

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/ParticleSystems.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/Culling.md)