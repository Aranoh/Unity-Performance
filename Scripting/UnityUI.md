# Unity UI  

Unity UI is niet het zuinigste systeem wat draait in Unity, al snel kan veel framerate verloren gaan door gebruik van Unity UI. Wel zijn er wat dingen 
die toegepast kunnen worden om toch een goede framerate te krijgen door het draaien van Unity UI.  

### Use Multiple canvases  

Unity UI maakt in eerste instantie gebruik van canvases, dit zijn verzamel objecten van UI onderdelen. Een nadeel van gebruik van deze canvases is dat 
wanneer een van de objecten op zo'n canvas verandert het alle andere objecten op dat canvas laat "rebuilden". Dit wil zeggen dat elk object op de canvas 
zijn layout opnieuw berekent, zijn meshes opnieuw genereerd en material's worden opnieuw gegenereerd vanwege batching.
