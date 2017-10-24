# Pooling
[terug naar index](/Index.md#scripting)  

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
weergegeven, ga op lowend devices er vanuit dat je 200mb of minder aan ram mag gebruiken.

gevonden test op IOS over maximum ram: [IOS ram test](/Scripting/RamTestIOS.md)

#### Memory spikes

Let als je objecten poolt met een groeiende pool, het kan voorkomen dat tijdens je spel deze pool veel groter word dan gepland. Als deze objecten hierna 
niet meer gebruikt worden kan je spreken van een "spike" in je pooling. Deze objecten zullen in de pool blijven staan en dus ook in het memory. Dit kan 
nadelige gevolgen hebben voor het memory verbruik van je game. Denk daarom van te voren goed na voordat je insteld dat je pool mag groeien of schrijf code 
om deze groei ook weer langzaam af te bouwen. 

### Gevaarlijke Componenten  

Niet alle componenten zijn even snel in gebruik als je ze wilt poolen. Sommige Unity componenten doen er langer over dan andere om geactiveerd en/of 
gedeactiveerd te worden.

Componenten waar op gelet moet worden zijn:

* AudioSource: Dit component opzich poolt vrij eenvoudig wel is het gebruik van 'PlayOnAwake' vrij langzaam waardoor poolen van AudioSource objecten traag kan voelen.
* WheelCollider: Dit component geeft een grote vertraging bij activeren, aan te raden om hier niet teveel mee te poolen.
* 2DColliders: Het gebruiken van meerdere 2D colliders op een gameObject kan traag worden met poolen van deze objecten. Activeren gaat vrij snel, maar deactiveren gaat exponentieel langzamer naar mate er meer colliders gebruikt worden in een object.


Test resultaten pooling test: [Pooling test](/Scripting/PoolingTest.md)  

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/UnityUI.md)[![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Scripting/GarbageCollector.md)
  
  