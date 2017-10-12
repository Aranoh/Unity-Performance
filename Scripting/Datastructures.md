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
 
|Big-O|operaties for 10 things|operaties for 100 things|Uitleg|
|:--:|:--:|:--:|:--:|
|O(1)|1|1|onafhankelijk van het aantal 'things' kost deze operatie altijd even veel|
|O(log(n))|3|7|een lijst constant te halveren tot bij het juiste object gekomen is|
|O(n)|10|100|aantal operaties achter de schermen is evenhoog als het aantal meegegeven 'things'|
|O(n log(n))|30|700|operaties groeien met log(n) afhankelijk van het aantal 'things' door bijvoorbeeld het sorteren van een lijst dmv het log(n) algoritme|
|O(n^2)|100|10000|aantal operaties groeit exponentieel met het aantal meegegeven 'things'|

<div>
* b.v. Vector3 of Quaternion
<br><br>
</div>   
#### Sub onderdeel

tekst van het sub onderdeel

[Cheat Sheet: Speed of Common Operations](/Scripting/CheatSheet.md)  

---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/UnityApiCalls.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/Scripting/UnityUI.md)