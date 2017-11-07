# Draw Calls & Batching
[terug naar index](/Index.md#unity-settings)  

Het tekenen van een object op het scherm gaat via 'Draw Calls'. Draw calls zijn te verglijken met een schilder die nieuwe (en andere) verf op zijn 
kwast doet om daarna weer iets moois te schilderen. Zo is in Unity elk object met een nieuwe material weer een nieuwe draw call om zo min mogelijk 
draw calls te krijgen in je scene moeten we weten waar extra draw calls vandaan komen.

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

 
### Frame debugger

tekst van het sub onderdeel


---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/ParticleSystems.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/Culling.md)