# Data Structures
[terug naar index](/Index.md#scripting)  

Binnen C# heb je veel verschillende data structures om te gebruiken. Niet elke data structure is even zuinig als andere. Probeer van te voren goed te bepalen 
welk van de verschillende data structures het bet past bij de implementatie die jij wenst. Om erachter te komen welk data structure het best gebruikt kan worden 
kunnen we een paar richtlijnen volgen.

## Actie Punten
* Weet de snelheid van de verschillende te gebruiken data structures
* Maak gebruik van verder genoemde richtlijnen
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

Het is bijna niet mogelijk om een complete lijst te geven van welk data structure het best te gebruiken is bij verschillend implementaties. Hieronder volgen een 
aantal voorbeelden van goede keuzes. Gebruik deze als richtlijnen.

###### List & Array
Onder de schermen niet veel meer dan een Array. Vaak een van de snellere data structures, gebruik list vooral voor snel ittereren en bijhouden van een niet 
te vaak veranderende collectie.  Wanneer de collectie helemaal of bijna niet veranderd kan ook goed gebruik gemaakt worden van een Array.

Gebruik bij ittereren bij voorkeur een for loop, deze zijn net wat sneller dan een foreach loop. Zorg wel dat je binnen de for loop het object 
uit je lijst even cached en dit cached object dan ook blijft gebruiken anders raak je de gewonnen snelheid van je for loop kwijt.  

###### Dictionary
Gebruikt de Hashtable class. Snel in gebruik als het gaat om constant toevoegen en verwijderen van objecten. Kan ook gebruikt worden om object te indexeren 
met een Key value. Let op met ittereren over een Dictionary dit is vanwege de onderliggende Hashtable niet een hele snelle operatie. 

###### Struct of Class + List
Alternatief voor een Dictionary is het gebruik van een List met hierin Struct's van verschillend objecten of gewoon een Class object, hiermee kan een relatie 
aangegeven worden tussen de objecten in dit Struct of Class en kan er snel over geittereerd worden. Structs hebben een lichtere memory footprint dan classes 
maar classes zijn reference typed in tegenstelling to een struct wat een value typed variabele is. Bedenk goed welke constructie het beste past bij 
wat er geimplementeerd moet worden.  

###### Gebruik meerdere datastructure
Soms kan het voorkomen dat je niet één datastructure kan vinden die het best past bij wat je wilt bereiken, in sommige gevallen kan het voordelig zijn om 
meer dan een datastructure te gebruiken, denk bijvoorbeeld aan het gebruiken van een List om snel over te ittereren en gebruik deze List i.c.m. een dictionary 
om te kunnen checken of het object al in de lijst bestaat of niet. Aangezien je in een game vast zit aan je 'update time' kan je met vergelijkbare trucjes 
extra framerate verkrijgen door het slim gebruiken van meerdere datastructures. Bedenk wel dat het gebruik van meerdere datastructures ook meer memory kost dus 
als je deze limiet tegen komt op je target device is het niet verstandig meer om dit te gebruiken.

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/UnityApiCalls.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Scripting/UnityUI.md)