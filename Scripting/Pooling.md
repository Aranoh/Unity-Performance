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

---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/UnityUI.md)[![Next Page](https://i.imgur.com/nHLTAf1.png)](/Scripting/GarbageCollector.md)
  
  