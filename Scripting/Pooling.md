# Pooling
[terug naar index](/Index.md)  

In games binnen Unit wordt veel gebruik gemaakt van prefabs. Het is eenvoudig om via script een prefab te spawnen in je game. Dit spawnen van prefabs gaat uiteraard niet helemaal kostenloos. 
Dit is de reden dat Pooling vaak gebruikt wordt in Unity. Object pooling kan ervoor zorgen dat je de druk van het objecten spawnen verlegd naar wanneer de game aan het opstarten is. 
Door tijdens opstarten alvast het maximaal te gebruiken objecten te "Poolen" kan je ervoor zorgen dat at runtime deze objecten gewoon klaarstaan voor gebruik. dit kan heel veel 
schelen in performance van je game.  

## Actie Punten
* OnEnable gebruiken ipv Start voor pooled objects
* Let op memory gebruik, pool geen onnodige dingen
* Let op voor "Spikes" van objecten als de pool hiermee vergroot deze blijven in memory staan (terwijl ze niet gebruikt meer worden)
##  

