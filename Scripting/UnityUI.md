# Unity UI  

Unity UI is niet het zuinigste systeem wat draait binne Unity, al snel kan veel framerate verloren gaan door verkeerd gebruik van Unity UI. Wel zijn er wat dingen 
die toegepast kunnen worden om toch een goede framerate te krijgen door het draaien van Unity UI.  

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

3d graphic raycasters  

### Camera.main  

