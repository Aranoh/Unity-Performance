# Data Structures
[terug naar index](/Index.md)  

Binnen C# heb je veel verschillende data structures om te gebruiken. Niet elke data structure is even zuinig als andere. Probeer van te voren goed te bepalen 
welk van de verschillende data structures het bet past bij de implementatie die jij wenst. Om erachter te komen welk data structure het best gebruikt kan worden 
kunnen we een paar richtlijnen volgen.

## Actie Punten
* Weet de snelheid van de verschillende te gebruiken data structures
* punt_twee_staat_hier
##  

### Snelheid 

Om de snelheid van een data structure te bepalen word gekeken naar de 'Big-O', met deze notatie word bepaald hoeveel operaties gedaan moeten worden ten opzichte van 
het aantal 'dingen' dat in de functie gestopt wordt.

Hieronder ter verduidelijking een tabel:
 
|Big-O|operaties voor 10 'things'|operaties voor 100 'things'|Uitleg / voorbeeld|
|:--:|:--:|:--:|:--:|
|O(1)|1|1|onafhankelijk van het aantal 'things' kost deze operatie altijd even veel|
|O(log(n))|3|7|een lijst constant te halveren tot bij het juiste object gekomen is|
|O(n)|10|100|aantal operaties achter de schermen is evenhoog als het aantal meegegeven 'things'|
|O(n log(n))|30|700|operaties groeien met log(n) afhankelijk van het aantal 'things' door bijvoorbeeld het sorteren van een lijst dmv het log(n) algoritme|
|O(n^2)|100|10000|aantal operaties groeit exponentieel met het aantal meegegeven 'things'|
  
#### Snelheid per operatie

Een Data structure heeft niet direct één snelheid, afhankelijk van de operatie is een data structure sneller of minder snel dan andere. Toegevoegd aan dit document 
is een 'Cheat Sheet' met hierin alle veel gebruikte operaties van data structures en de snelheid hiervan.

[Cheat Sheet: Speed of Common Operations](/Scripting/CheatSheet.md)  

### Aanbevolen Data structures

Het is bijna niet mogelijk om een complete lijst te geven van welk data structure het best te gebruiken is bij verschillend gebruik. Hieronder volgen een 
aantal voorbeelden van goede keuzes. Gebruik deze als richtlijnen.

doe je dit gebruik dan dit
doe je zus gebruik dan zo

---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/UnityApiCalls.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/Scripting/UnityUI.md)