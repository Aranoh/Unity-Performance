# Unity UI
[terug naar index](/Index.md)  
Unity UI is niet het zuinigste systeem wat draait binne Unity, al snel kan veel framerate verloren gaan door verkeerd gebruik van Unity UI. Wel zijn er wat dingen 
die toegepast kunnen worden om toch een goede framerate te krijgen door het draaien van Unity UI.  

## Actie Punten
* Gebruik los canvas voor static and dynamic objecten
* Graphic raycasters niet gebruiken wanneer niet nodig
* Let op render/event camera in te stellen
* Gebruik Anchors in plaats van Layout groepen
* Slim objecten poolen door disablen elementen voor reparenting
##  

### Use Multiple canvases  

Unity UI maakt in eerste instantie gebruik van canvases, dit zijn verzamel objecten van UI onderdelen. Een nadeel van gebruik van deze canvases is dat 
wanneer een van de objecten op zo'n canvas verandert het alle andere objecten op dat canvas laat "rebuilden". Dit wil zeggen dat elk object op de canvas 
zijn layout opnieuw berekent, zijn meshes opnieuw genereerd en material's worden opnieuw gegenereerd vanwege batching.

Het splitsen van je UI elementen in minstens 2 canvases is een goed startpunt hiervoor. zo heb je er een met alle static objecten en een met dynamic objecten. 
met het veranderen van een object op het ene canvas blijft je andere canvas gewoon onaangetast. dit zorgd ervoor dat dit deel van je canvas niet opnieuw hoeft te rebuilden.  

Met het gebruik van meerdere canvases kan wel gebruik gemaakt worden van een 'nested canvas' een zo een canvas neemt de render mode van zijn parent over waardoor 
je dus geen problemen hoeft te krijgen met alignen van je verschillende canvases.  

### Graphic Raycaster

Een graphic raycaster wordt gebruikt om screen/touch input te regelen op je canvas, dit object is bedoeld om input mogelijk te maken op verschillende UI elementen. 
een graphic raycaster zit standaard op elk UI onderdeel dat Unity gebruikt. dit is echter overbodig en zorgd op zijn beurt ook weer voor performance loss. Dit 
aangezien bij elke druk/klik op het scherm al deze raycasters gechecked worden is het verstandig deze uit te zetten op objecten die geen input nodig hebben.    

### Render en event camera 

Op een canvas word van je verwacht dat je een camera insteld ofwel als render camera voor screen space canvases of als event camera voor world space canvases.  

Aan te raden is hier altijd een camera in te stellen. wanneer dit niet gedaan word zal unity zelf naar de Camera.main vragen om deze te gebruiken, soms wel meerdere 
keren per frame.  

Waarom gebruik van Camera.main zo traag is is terug te vinden op de _[UnityApiCalls](/Scripting/UnityApiCalls.md)_ pagina onder het kopje "Caching Unity Objects".  

### Layout Groups  

Layout groepen zitten met ongeveer het zelfde probleem als canvases door het veranderen van een object in een Layout groep word heel het layout system doorgezocht 
met 'GetComponent' calls dit maakt het gebruiken van meerdere nested Layout objecten niet echt performance gericht. Probeer dus ook zo min mogelijk gebruik te maken 
van deze layout groepen. Mocht je toch graag gebruik willen maken van schalende dingen op je scherm, maak dan slim gebruik van 'Anchor points', hiermee kan veel 
van de funcionaliteit van layout groepen goed nagedaan worden.

### UI Object pooling  

Object pooling kan bij UI net als bij 3D games best wel wat performance schelen. Voor bijvoorbeeld het gebruik van scroll lists in je inventory scherm of voor terugkomende UI objecten in een 
2D game is het mogelijk om object pooling te gebruiken. Object pooling werkt in UI hetzelfde als met 3D objecten.  

Om ervoor te zorgen dat je zo min mogelijk objecten "dirty" maakt is het aan te raden om eerst een object te disablen voordat je het gaat verplaatsen in de hierarchie 
Dit zorgd ervoor dat alleen het oude parent object "dirty" wordt en het nieuwe objec wordt pas dirty als je het object enabled.
Ook is het verstandig om eerst alle waardes te veranderen van het object voordat je het enabled. Ook dit zorgd voor minder "dirty" maken van het nieuwe canvas.

Voor meer info over object pooling bekijk de wiki pagina over [Pooling](/Scripting/Pooling.md). 