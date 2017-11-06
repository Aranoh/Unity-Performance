# Textures
[terug naar index](/Index.md#unity-settings)  

Deze wiki gaat zowel over het maken van textures als het gebruiken van textures binnen Unity, het geeft een paar richtlijnen waaraan gedacht kan 
worden zodat een mooi uitziende game gemaakt kan worden zonder performance problemen.  

## Actie Punten
* Weet hoe groot je textures in het scherm komen zodat niet te grote textures gemaakt hoeven worden
* Gebruik 'Mipmaps' visualisatie om te grote textures te visualiseren
* Ken de verschillende compressie formaten van Unity
##  

### Texture Groote 

Denk bij het maken van textures er altijd aan dat ze nooit volledig op het scherm zullen komen. Het heeft dus ook niet zoveel zin om 2048 bij 2048 textures 
te maken voor een scherm wat maar 1920 bij 1080 is. Op mobile is dit uiteraard nog minder nodig aangezien je maar naar een klein scherm zit te kijken.  

Denk er bij het maken van een texture over na hoe groot dit texture op het scherm zal komen. als het gaat over een schermvullend object kan hiervoor 
een hoge resolutie texture gemaakt worden. wanneer een object maar 10% de schermhoogte zal gebruiken is het niet nodig om hier 2048 pixels te gebruiken. 
Probeer een texture groote te pakken die op het scherm dicht tegen een 'texel per pixel' zal zitten. Dit wil zeggen dat een 10x10 texture op 10x10 pixels 
op het scherm weergegeven wordt. 

### Mipmaps visualisatie

Unity heeft de mogelijkheid om in een scene aan te geven waar je teveel 'texels per pixel' gebruikt. Dit werkt door in de scene view de 'mipmap' 
visualisatie aan te zetten. Met deze visualisatie wordt kleur gebruikt om aan te geven welke objecten teveel pixels bevatten. Deze objecten worden 
in het rood aangegeven. Probeer voor deze objecten een minder grote texture te gebruiken, eventueel kan dit met LOD gedaan worden als objecten zowel 
dichtbij als verweg weergegeven worden.

mipmap visualisatie:  

![Textures_mipmap_normal](/Afbeeldingen/Textures_mipmap_normal.png)  

Gebruik van LOD om meer blau te krijgen in de mipmap visualisatie:  

![Textures_mipmap_LOD](/Afbeeldingen/Textures_mipmap_LOD.png)  


---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/DrawCallsBatching.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/Culling.md)