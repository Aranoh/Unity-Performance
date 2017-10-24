# Culling
[terug naar index](/Index.md#unity-settings)  

Culling is de naam die gegeven word aan het 'verbergen' van objecten die buiten de camera grenzen vallen. Aangezien je deze objecten toch niet kan zien 
is het ook niet nuttig om ze te renderen of scripts te laten draaien op deze objecten. Door culling toe te passen op verschillende manier kan je ervoor 
zorgen dat alleen zichtbare dingen invloed hebben op je game performance en dat niet zichtbare objecten gedeactiveerd worden.  

## Actie Punten
* Gebruik occlusion culling op static objecten
* Maak gebruik van 'CullingGroup' voor meer custom culling
##  

### Occlusion culling 

Unity's standaard culling wordt via de occlusion culling gedaan. Occlusion culling kan een scene scannen op alle verschillende objecten met renderers. 
Occlusion culling heeft de mogelijkheid deze objecten te 'baken' en data opslaan van wanneer deze objecten wel en niet zichtbaar zouden zijn. Door gebruik 
van deze functionaliteit kan met grote omgevingen in je Unity game toch een goede framerate gehaald worden omdat niet alles zichtbaar is.  

#### Stappen plan

##### Static objecten aangeven voor culling
/Afbeeldingen/

Niet alle objecten worden automatish meegenomen in occlusion culling. Om in object te omvatten in de culling moet deze gemarkeerd worden als 'static', dit 
wordt gedaan rechts boven in de inspector door het aanvinken van deze optie.  
![Static](/Afbeeldingen/Culling_Static.png)  

##### Openen culling scherm

Navigeer naar het culling scherm, dit scherm is te vinden onder 'Window' en dan 'Occlusion Culling'.  
![Navigeer](/Afbeeldingen/Culling_Navigatie.png)  

##### Instellingen Culling
In het Occlusion culling scherm onder het tabblad 'bake' zitten wat opties. De standaard opties zijn over het algemeen goed voor elke scene. Eerste tween opties 
gaan over de hoe groot gaten en blokken die visie doorlaten en blokkeren kunnen zijn. de derde en laatste optie is een optie om ook 'backfaces' mee te nemen in 
de occlusion culling zodat ook deze niet zichtbaar zijn als tegen de voorkant van een object aangekeken wordt.  
![Options](/Afbeeldingen/Culling_Opties.png)  

##### Baking

Laatste stap is het bakken van je occlusion data met deze scene. Dit kan afhankelijk van de groote van je scene en de gekozen opties lang of kort duren. 
Probeer tijdens development altijd voor opties te kiezen die snel zijn, met elke verandering in je scene moet namelijk opnieuw de occlusion gebakken worden. 
Later richting een release build kan wanneer nodig altijd nog met meer precisie gescand worden.  
![Baking](/Afbeeldingen/Culling_Baking.png)  

##### Opmerkingen

* Let op dat je scene is opgeslagen, zonder opgeslagen scene kan er geen occlusion gebakken worden.
* Zorg voor trees op Unity Terrain dat de prefabs op static staan anders worden ze niet meegenomen tijdens bakken.
* Er wordt altijd in een cube gescand. Een enkele losse vogel hoog in je scene of vis heel laag kan de baktijd flink beinvloeden.  

### Culling Groups

Een tweede vorm van culling is het gebruik maken van Unity's 'CullingGroup' met deze CullingGroup kunnen objecten die normaal niet binnen de occlusion 
culling vallen toch meedoen met dit systeem. CullingGroup is standaard alleen vanuit script te gebruiken er zijn hier standaard geen components voor. 
Hieronder een aantal code stukjes met een voorbeeld van hoe CullingGroup gebruikt kan worden. Meer informatie kan gevonden worden in de UnityDocs.  

_[UnityDocs: CullingGroupAPI](https://docs.unity3d.com/Manual/CullingGroupAPI.html)_  
_[UnityDocs: CullingGroup](https://docs.unity3d.com/ScriptReference/CullingGroup.html)_  

**Aanmaken CullingGroup**  
Om een CullingGroup goed te gebruiken moet het op een juiste manier geïnitialiseerd worden.  
```C#
public float cullingRadius = 1;
CullingGroup cullingGroup;
	
void Start ()
{
	//Creating new CullingGroup and setting values
	cullingGroup = new CullingGroup();
	cullingGroup.targetCamera = Camera.main;
	cullingGroup.SetBoundingSpheres(new[] { new BoundingSphere(transform.position, cullingRadius) });
	cullingGroup.SetBoundingSphereCount(1);
	//Setting the onStateChanged function
	cullingGroup.onStateChanged += OnStateChanged;
}
```  
**OnStateChanged**  
Een eigen gedefineerde functie kan gemaakt worden die aangeroepen wordt wanneer de BoundingSphere van het object binnen of buiten het camera beeld valt.  
```C#
void OnStateChanged(CullingGroupEvent sphere)
{
	if (sphere.hasBecomeVisible)
	{
		//Reactivate components on this object
	}
	else
	{
		//Deactivate components on this object
	}
}
```  
**OnDestroy**    
Om garbage opstapeling te voorkomen zorg voor een goede OnDestroy functie die de cullingGroup's op een goede manier weggooit.  
```C#
void OnDestroy()
{
	// To clean up the CullingGroup and free all memory it uses,
	// dispose of the CullingGroup via the standard .NET IDisposable mechanism.
	if (cullingGroup != null)
	cullingGroup.Dispose();
}
```  
**OnDrawGizmos**  
Als hulp kan in de editor een 'Gizmo' getekend worden om de BoundingSphere van het object aan te geven.  
```C#
void OnDrawGizmos()
{
	if (enabled)
	{
		if (cullingGroup != null)
		{
			Gizmos.color = cullingGroup.IsVisible(0) ? Color.green : Color.gray;
		}
		else
		{
			Gizmos.color = Color.blue;
		}
		Gizmos.DrawWireSphere(transform.position, cullingRadius);
	}
}
```  

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/Textures.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/Audio.md)