# Unity API calls

Met het gebruik van Unity API calls moet je altijd goed opletten. Je weet van tevoren vaak niet wat er achter de schermen gebeurd. 
Iets wat lijkt een makkelijke functie aanroep te zijn in Unity kan achter de schermen voor behoorlijk wat framerate loss of garbage allocation 
zorgen. Om een complete lijst met API calls te geven die achter de schermen te druk zijn om te gebruiken in een update loop is bijna niet te doen. 
Development van Unity staat ook niet stil dus deze lijst van functies zal constant veranderen. Met behulp van Unity profiling zou je er snel achter 
moeten komen waar je teveel gebruik maakt van zware API calls. Door het op een slimme manier omschrijven van je code kan veel van de zware code 
weg gewerkt worden zodat het geen framerate meer hoeft te kosten.

### Array returning API calls
Door het gebruik API calls die Arrays teruggeven kan snel veel framerate verloren gaan, vooral als dit in een 'update loop' gebeurd. 
Unity maakt met het teruggeven van een array een nieuwe kopie aan van deze array. dit kan dus snel voor veel garbage zorgen.
Het is aan te raden deze functies niet in een 'update loop' te gebruiken of naar alternatieven te zoeken.  

Hieronder een paar voorbeelden van werkwijzen die toegepast kunnen worden:

#### Zoeken alternatieven  

##### Touch input
```C#
void Update() 
{
	foreach (Touch touch in Input.touches) 
	{
		if (touch.phase != TouchPhase.Ended && touch.phase != TouchPhase.Canceled)
		// DO SOMETHING      
	}
}
```  
[Unity Docs Input.touches](https://docs.unity3d.com/ScriptReference/Input-touches.html)

Bovenstaand stuk code maakt gebruik van de Input.touches die hier in dit geval elke frame garbage creëert. Hieronder is een alternatief gegeven die gebruik maakt van 
Input.touchCount en Input.getTouch() om zo presies het zelfde te doen als bovenstaande code.  
```C#
void Update() 
{
	for (int i = 0; i <= Input.touchCount; i++)
	{
		if (Input.GetTouch(i).phase != TouchPhase.Ended && Input.GetTouch(i).phase != TouchPhase.Canceled)
		// DO SOMETHING
	}     
}
```

[Unity Docs Input.GetTouch()](https://docs.unity3d.com/ScriptReference/Input.GetTouch.html)  
[Unity Docs Input.touchCount](https://docs.unity3d.com/ScriptReference/Input-touchCount.html)
#### NonAlloc versies

Sommige API calls in Unity hebben een speciale functie die geen garbage creëert, deze alternatieven werken vaak presies het zelfde als de 'normale' versies 
Maar zijn beter te gebruiken in een 'update loop' die vaak vrij performance gevoelig zijn.  
hieronder een voorbeeld van SphereCastAll en zijn alternatief SphereCastAllNonAlloc:

```C#
RaycastHit[] hitInfos;

void Update() 
{
	hitInfos = SphereCastAll(origin, radius, direction, maxDistance, layerMask, queryTriggerInteraction);

	foreach(RaycastHit hit in hitInfos)
	{
		if (hit.distance > 0)
		//DO SOMETHING
	}
}
```  
Onderstaand voorbeeld gebruikt de NonAlloc versie van deze functie om zo een bestaande array te vullen in plaats van te vervangen.
Als van te voren bekend is hoe groot de terugkomende array maximaal kan zijn kan hierop ingespeeld worden door deze array met dit formaat aan te maken. 
Hierdoor kan gezorgd worden dat er nooit garbage gemaakt word bij aanroepen van deze functie.  
```C#
RaycastHit[maxHits] hitInfos;

void Update() 
{
	SphereCastNonAlloc(origin, radius, direction, hitInfos, maxDistance, layerMask, queryTriggerInteraction);

	foreach(RaycastHit hit in hitInfos)
	{
		if (hit.distance > 0)
		//DO SOMETHING
	}
}
```
#### Caching values

Binnen Unity bestaan Onderdelen die in eerste instantie makkelijk te gebruiken lijken maar die 