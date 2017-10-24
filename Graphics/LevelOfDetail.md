# Level Of Detail
[terug naar index](/Index.md#graphics)  

Waneer een GameObject verweg staat van de camera kan je nog moeilijk alle details zien van dit object. Wel is zo dat standaard alle polygons wel getekend 
worden. Dit kan je veel performance kosten als er veel objecten zijn die verweg staan van de camera. Om dit te kunnen verkomen kan gewerkt worden met Level of Detail 
(LOD) om objecten verder weg van de camera met minder polygonen te kunnen renderen.  

## Actie Punten
* Leer omgaan met Unity's Level Of Detail systeem  
* Level of Detail models maken voor gebruik in Unity
##  

### Unity LOD 

Unity LOD systeem is volledig te gebruiken via de Editor. Je hebt hier geen code voor nodig. Unity LOD systeem maakt gebruik van 'LODGroups' waarmee in te stellen 
is wanneer een object naar een hoger of lager LOD mesh over zal springen. Met LODGroups kan ingesteld worden wanneer een ander LOD mesh gerenderd moet worden 
dit word veranderd afhankelijk van de vulling van je object ten opzichte van je scherm.
#### Sub onderdeel

tekst van het sub onderdeel

![IMAGE](/Afbeeldingen/LOD-cull-scherm.png)  
![IMAGE2](/Afbeeldingen/test.png)  
![Image](PS-MinMaxCurve(cut).png)  



[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LowDetailCamera.md)
---