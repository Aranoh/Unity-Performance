# Pooling
[terug naar index](/Index.md)  

In games binnen Unit wordt veel gebruik gemaakt van prefabs. Het is eenvoudig om via script een prefab te spawnen in je game. Dit spawnen van prefabs gaat uiteraard niet helemaal kosteloos. 
Dit is de reden dat Pooling vaak gebruikt wordt in Unity. Object pooling kan ervoor zorgen dat je de druk van het objecten spawnen verlegd naar wanneer de game aan het opstarten is. 
Door tijdens opstarten alvast het maximaal te gebruiken objecten te "Poolen" kan je ervoor zorgen dat 'at runtime' deze objecten gewoon klaarstaan voor gebruik. Dit kan heel veel 
schelen in performance van je game.  

## Actie Punten
* OnEnable gebruiken i.p.v. Start voor pooled objects
* Let op memory gebruik, pool geen onnodige objecten
* Let op voor "Spikes" van objecten aantallen, als de pool hiermee vergroot wordt blijven deze objecten in memory staan (terwijl ze niet meer gebruikt worden)
##  


### OnEnable

gepoolde objecten zullen niet via de 'Start' methode lopen. gebruik voor objecten die je wilt poolen de 'OnEnable' functie om het object te initialiseren, zorg 
dat je in deze OnEnable alle waardes terug op zijn standaard waardes zet zodat het game object 'als nieuw' is en gebruikt kan worden waar het voor bedoeld is.  

### Memory Gebruik  

Het nadeel van objecten poolen is dat deze objecten constant in het memory zullen staan. Op pc is dit vaak niet zo'n probleem omdat deze vaak over veel RAM 
beschikken maar op mobile moet je wel opletten dat je niet teveel objecten poolt dat je over de limits heen gaat van het device. Dit kunnen de hardware limits zijn 
maar veel apparaten hebben ook een ingebouwde software limit die het maximaal aantal ram per app limiteert. Dit verschilt per device en is nergens officieel 
weergegeven, ga op lowend devices er vanuit dat je 200mb aan ram mag gebruiken.

gevonden test op IOS over maximum ram: [IOS ram test](/Scripting/RamTestIOS.md)


---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/UnityUI.md)[![Next Page](https://i.imgur.com/nHLTAf1.png)](/Scripting/GarbageCollector.md)
  
  