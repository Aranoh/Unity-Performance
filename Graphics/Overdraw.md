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
Elke shader heeft zijn eigen 'RenderType tag'. Er zijn een aantal verschillende tags die te gebruiken zijn en buiten dat kan je ook getallen instellen 
voor de render que volgorde. Elke 'RenderType tag' heeft ook zijn eigen int waarde.  

Hieronder een overzicht van de verschillende tags en de waardes die hieraan gegeven zijn:  

* Background (1000)  
Gebruikt voor de achtergrond en voor objecten die ver in de achtergrond bijven staan. Vanwege lage queue nummer vaak als laatste getekend.  

* Geometry (2000)  
Wordt gebruikt voor de normale niet transparante objecten in je spel.  

* AlphaTest (2450)  
Gebruikt voor alpha test geometry objecten.  

* Transparent (3000)  
Gebruikt in transparante objecten. Objecten in deze queue worden van achter naar voor getekend ipv van voor naar achter.  

* Overlay (4000)  
Gebruikt voor overlay objecten. 

Door shaders of objecten zo veel mogelijk in te stellen dat alles van voor naar achter getekend wordt zal je zo min mogelijk overdraw krijgen in 
je scene. De grafische kaart is zo ingesteld dat hij een object achter een ander object niet zal renderen (minst het in dezelfde queue bevind). 
Hierdoor kunnen we vooraan beginnen met tekenen en zo overdraw voorkomen door het niet of maar half tekenen van objecten in de achtergrond. 
Het toevoegen van veel objecten in de 'Transparent' queue zal zorgen voor extra overdraw, deze objecten moeten over elkaar getekend worden om te 
garanderen dat alle transparante objecten zichtbaar zijn ookal staan ze achter ander transparante objecten. Ga hier verstandig mee om.

In je shader kan de RenderType tag worden aangepast:  

```
SubShader
{
	Tags { "RenderType"="Transparent" }
	// Rest of shader code
```

Ook in C# kan het render queue nummer worden aangepast:

```c#
public float queue;
public GameObject cube;

cube.GetComponent<MeshRenderer>().material.renderQueue = queue;
```
 

### Overdraw visualisatie

Overdraw kunnen we niet direct zien in een normale scene. Het is mogelijk te onderzoeken waar overdraw zich kan gaan bevinden maar het is vaak 
makkelijker om overdraw visueel te maken zodat snel gezien kan worden waar overdraw zich bevind en waar het te voorkomen valt.

##### Unity Overdraw  

Unity overdraw is niet een visualisatie van hoe overdraw werkt. Het kan gebruikt worden om gevaarlijke delen snel te zien en overdraw te voorkomen 
voordat je dit echt gaat testen maar Unity heeft geen echte overdraw visualisatie. Wat Unity doet is alle objecten in een scene vervangen door een 
transparante mesh van hetzelfde model. door een complete scene op te bouwen uit dit soort objecten kan gezien worden waar veel objecten over 
elkaar heen komen te staan. Let erop dat dit nog geen overdraw is maar wel kan van plekken waar veel objecten over elkaar heen staan overdraw ontstaan.  

Je vindt de overdraw feature van Unity in de scene view onder render instellingen:  

![Overdraw_Unity_Settings](/Afbeeldingen/Overdraw_Unity_Settings.png)  

Overdraw in een Unity scene:  

![Overdraw_Unity_Screen](/Afbeeldingen/Overdraw_Unity_Screen.png)  

##### Intell Graphics performance Analyzer  

Om een betere visualisatie van overdraw te krijgen is aan te raden om hier een tool voor te installeren. De tool die ik gebruikt heb hiervoor en 
de tool die ook zal willen aanraden om zelf te gebruiken in de GPA van intell. 

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/ShadersPostProcessing.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/Polycount.md)