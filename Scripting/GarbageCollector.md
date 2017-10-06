# Garbage Collecor
[terug naar index](/Index.md)  

Door het draaien van je spel zal steeds meer data in je memory opgeslagen worden. De garbage collector speelt hier op in door om de zoveel tijd een keer heel 
je memory door te lezen en alle niet gebruikte data weer vrij te maken voor gebruik. Dit gaat uiteraard niet zonder kosten en daarom is het verstandig om 
zo min mogelijk "data te alloceren" tijdens het draaien van je spel. Hoe minder de garbage collector hoeft te draaien hoe minder performance het je kost bij je game.  

## Actie Punten
* Weten verschil 'Stack' en 'Heap' memory en welke waardes waarin komen
* Cashing data om niet elke frame memory te hoeven allocaten
* Zuinig omgaan met gebruik garbage makende methode's
* Draai 'dure' code niet elke frame maar op een timer
* Hergebruiken van collecties
* Gebruik Stringbuilder in de plaats van String voor minder garbage
* Let op bij Unity API calls die garbage maken
* 'Boxing' van waardes creert garbage, let op bij gebruik
* Voorkom aanmaken van garbage bij yields in coroutines
##  

### Heap VS Stack 

Binnen Unity worden twee verschillende soorten memory gebruikt. Elke variabele die aangemaakt wordt zal op een van deze twee 'pools' terecht komen. Welke pool 
gebruikt wordt hangt af van wat voor soort object er in het memory gezet wordt.  
Stack memory is snel en gemakkelijk. Memory op de stack word direct vrij gemaakt zodra een object 'buiten de scope' valt.  
Heap memory is iets ingewikkelder. Heap memory word pas leeg gehaald als de garbage collector hier overheen kijkt.  

Hoe heap memory werkt:
* wanneer een variabele op de heap gezet wil worden zal eerst gekeken worden of er genoeg plaats is
* Als er niet genoeg plaats is zal de garbage collector draaien om plaats te maken voor dit object
* Soms is er na het draaien van de collector nog steeds niet genoeg plek, de heap memory zal dan vergroten

Stappen garbage collector:
* Garbage collector bekijkt elk object op de heap
* Voor elk bekeken object bepaald de garbage collector of het object nog binnen de scope valt
* Elk object dat buiten scope valt word getagd voor verwijderen
* getagde objecten worden uit de heap gehaald en dit deel memory is dan weer vrij

Wanneer draait de garbage collector:
* Als een stuk data op de heap gezet wil worden maar er niet genoeg vrije ruimte is op dit deel memory
* Om de zoveel tijd zal Unity de garbage collector automatish aanroepen
* Wanneer dit zelf gedaan word uit code

Aanroepen garbage collector:
```c#
System.GC.Collect();
```
[MSDN: GC.Collect](https://msdn.microsoft.com/en-us/library/xe0c2357(v=vs.110).aspx)

Het is wel zo dat memory op de heap door veel alloceren en dealloceren van memory 'fragmented' raakt, dit wil zeggen dat er lege stukken in je heap zullen vallen 
die niet zo makkelijk meer gebruikt kunnen worden. Dit is een goede reden om goed op te letten op je memory allocatie om dit te voorkomen.


#### Value typed VS reference typed

Er word onderscheid gemaakt tussen twee verschillende variabelen, je hebt de 'Value-typed local variables', deze variabelen komen op de stack terecht. Naast deze 
type heb je ook de 'Reference types' deze types komen op de heap terecht. 


|Value types|Reference types|
|:--:|:--:|
|int|Classes|
|float|Transform|
|double|GameObject|
|bool||
|char||
|Structs*||

<div>
* b.v. Vector3 of Quaternion \n
</div>  
 
tekst van het sub onderdeel


---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Index.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/Index.md)