# Overdraw
[terug naar index](/Index.md#graphics)  

Overdraw is de term die gebruikt wordt als een pixel meerdere keren getekend wordt op je scherm. Dit gebeurd als er meerdere dingen over elkaar 
gerendered worden in een scene. Om overdraw zo veel mogelijk te voorkomen moeten we weten waardoor dit allemaal komt zodat hier op ingespeeld 
kan worden.  

## Actie Punten
* Weet waar overdraw vandaan kan komen
* Weet tools te gebruiken om overdraw visueel te maken
* Weet overdraw te voorkomen door middel van het instellen van een goede draw order

##  

### Overdraw 

Overdraw komt in je spel door het verkeerd ordenen van je render queue, de render queue volgorde in Unity wordt bepaald door de shader. Je wil 
je objecten het liefst zo instellen dat alles van voor naar achter getekend wordt. Door objecten van voor naar achter te tekenen kan een object 
in de achtergrond kijken welk object er al voor hem in het scherm staan en op deze plekken word het object in de achtergrond dan niet getekend. 
Elke shader heeft zijn eigen 'Queue tag'. Er zijn een aantal verschillende tags die te gebruiken zijn en buiten dat kan je ook getallen instellen 
voor de render que volgorde. Elke 'Queue tag' heeft ook zijn eigen int waarde.  

Hieronder een overzicht van de verschillende tags en de waardes die hieraan gegeven zijn:  

* Background (1000)  
Gebruikt voor de achtergrond en voor objecten die ver in de achtergrond bijven staan. Vanwege lage queue nummer vaak als laatste getekend.  
* Geometry (2000)  
Wordt gebruikt voor de normale niet transparante objecten in je spel. 
* AlphaTest (2450)  
Gebruikt voor alpha test geometry objecten
* Transparent (3000)  
Gebruikt in transparante objecten. Objecten in deze queue worden van achter naar voor getekend ipv van voor naar achter.
* Overlay (4000)  
Gebruikt voor overlay objecten. 

#### Sub onderdeel

tekst van het sub onderdeel


---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/ShadersPostProcessing.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/Polycount.md)