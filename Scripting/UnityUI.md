# Unity UI  

Unity UI is niet het zuinigste systeem wat draait binne Unity, al snel kan veel framerate verloren gaan door verkeerd gebruik van Unity UI. Wel zijn er wat dingen 
die toegepast kunnen worden om toch een goede framerate te krijgen door het draaien van Unity UI.  

## Actie Punten
* Gebruik Canvas voor static and dynamic objecten
* Graphic raycasters niet gebruiken wanneer niet nodig
* Let op render/event camera in te stellen
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

### Camera.main  

Op een canvas word van je verwacht dat je een camera insteld ofwel als render camera voor screen space canvases of als event camera voor world space canvases.  

Aan te raden is hier altijd een camera in te stellen. wanneer dit niet gedaan word zal unity zelf naar de Camera.main vragen om deze te gebruiken, soms wel meerdere 
keren per frame.  

Waarom gebruik van Camera.main zo traag is is terug te vinden op de _[UnityApiCalls](/Scripting/UnityApiCalls.md)_ pagina onder het kopje "Caching Unity Objects".  

### Layout Groups  

Layout groepen zitten met ongeveer het zelfde probleem als canvases door het veranderen van een object in een Layout groep word aanpassingen gedaan op al 
de bovenliggende layout groepen in de hiërarchie 

