# Particle Systems
[terug naar index](/Index.md#graphics)  

Deze pagina gaat het hebben over Particle Systems en hoe hier optimaal gebruik gemaakt van kan worden.  

## Actie Punten
* Ben bewust van performance impact van verschillende modules
* betrek je particle systemen in de culling van je game
* Gebruik op een goede manier de particle system functies
##  


### Performance Modules

Binnen particle systems heb je een hele set verschillende modules die ieder iets anders doen met hoe het particle systeem eruit ziet. Deze verschillende systemen 
hebben ook allen hun eigen performance kenmerken. niet elk systeem is even snel als een ander systeem.

Om een beeld te krijgen van hoe de verschillende systemen invloed hebben op de performance van je game staan hier onder wat grafieken, hierin worden instellingen 
en features getest op performance.

![Module Performance](/Afbeeldingen/PS_Module_Performance_small.png)  
![MinMaxCurve](/Afbeeldingen/PS_MinMaxCurve_small.png)  
![MinMaxGradient](/Afbeeldingen/PS_MinMaxGradient_small.png)  
![Shape Module](/Afbeeldingen/PS_Shape_Module_small.png)  


#### extra informatie
Bovenstaande grafieken komen uit een demonstratie van de nieuwe particle systemen van Unity 2017, om een beter beeld te krijgen van wat de verschillende systemen
voor mogelijkheden hebben raad ik aan een keer te kijken naar dit demo project of presentatie.

[![Video](/Afbeeldingen/PS_Youtube_Video.png)](https://www.youtube.com/watch?v=_N4iL0SQ9q8)  

[Download project](http://bit.ly/2ueFDWF)  

### Particle system culling

Particle system kan met de nieuwe versie van Unity door gebruik te maken van de culling groups. Hierover kan je meer vinden op de pagina over _[Culling](/UnitySettings/Culling.md)_ 
, hieronder een klein voorbeeld specifiek voor het activeren en deactiveren van alle particle systems van een object.


```c#
void OnStateChanged(CullingGroupEvent sphere)
{
	if (sphere.hasBecomeVisible)
	{
		// Resume the system when we become visible.
		particleSystems.ForEach(ps => ps.Play(true));
	}
	else
	{
		// When we are culled we shall pause all systems.
		particleSystems.ForEach(ps => ps.Pause());
	}
}
```

### Scripting  

Start en Stop calls op een particle systeem loopt standaard door alle children heen om hierin ook particle systems aan en uit te zetten. Wanneer dit niet nodig is gebruik dan 'false' 
voor de 'withChildren' parameter. Dit scheelt je wat performance voor het aan en uitzetten.

Mocht je toch graag alle children uit of aan willen zetten cache dan zelf de lijst van parent en child particle systems en roep deze allemaal aan met Start of Stop. Door cachen is 
deze methode sneller dan Unity's implementatie.

[Unity Docs: ParticleSystem.Play](https://docs.unity3d.com/ScriptReference/ParticleSystem.Play.html)  
[Unity Docs: ParticleSystem.Stop](https://docs.unity3d.com/ScriptReference/ParticleSystem.Stop.html)  

Note voor Unity 5.4 tot 2017.2:  
_Stop en Start alloceren memory zelfs als het particle systeem al draait of gestopt is, dit is een 'bug'. Mogelijk kan een extention geschreven worden 
om de internal functies aan te roepen, of d.m.v. reflection aanroepen van deze functies. Alleen aan te raden wanneer upgrade naar 2017.2 te ver weg is._ 

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/Textures.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/DrawCallsBatching.md)