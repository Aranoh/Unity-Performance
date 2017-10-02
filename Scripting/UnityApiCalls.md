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
[Unity Docs: Input.touches](https://docs.unity3d.com/ScriptReference/Input-touches.html)

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

[Unity Docs: Input.GetTouch()](https://docs.unity3d.com/ScriptReference/Input.GetTouch.html)  
[Unity Docs: Input.touchCount](https://docs.unity3d.com/ScriptReference/Input-touchCount.html)  

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
[Unity Docs: Physics.SphereCastAll](https://docs.unity3d.com/ScriptReference/Physics.SphereCastAll.html)  
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
[Unity Docs: Physics.SphereCastNonAlloc](https://docs.unity3d.com/ScriptReference/Physics.SphereCastNonAlloc.html)   

Een tweede voorbeeld is het gebruik van "GetComponents" dit geeft een lijst terug van alle gevonden resultaten binnen het aangegeven kader. GetComponents heeft twee 
versies waarmee gewerkt kan worden. De tweede versie heeft een return value binnen de functie die van te voren aangemaakt kan worden en dus geen garbage meer creëert 
op het moment van aanroepen.

```c#
void Start()
    {
        HingeJoint[] hingeJoints;

        hingeJoints = GetComponents<HingeJoint>();

        foreach (HingeJoint joint in hingeJoints)
            joint.useSpring = false;
    }
```  

Betere versie hier onder weergegeven:  

```c#
 void Start()
    {
        // Disable the spring on all HingeJoints in this game object
        List<Component> hingeJoints = new List<Component>();

        GetComponents(typeof(HingeJoint), hingeJoints);

        foreach (HingeJoint joint in hingeJoints)
            joint.useSpring = false;
    }
```   

#### Caching Unity Objects

Niet alle Objecten of value's die je via Unity opvraagd worden gecached binnen het Unity systeem, aan te raden is dan ook om dit zelf te doen.  

Een van de meest gebruikte voorbeelden van zo'n niet gecachede waarde is het gebruik van Camera.main, dit lijkt in eerste instantie een simpele 
aanroep naar de main camera van Unity maar achter de schermen maakt deze API call gebruik van "FindGameObjectWithTag" die door alle GameObjecten 
in de scene zoekt naar de tag "maincamera". Aan te raden is dus om zo veel mogelijk objecten te cachen vooral als je niet weet hoe Unity aan deze 
waarden komt.  

Denk er bij cachen van waardes wel altijd aan dat deze waardes kunnen veranderen, er kan bijvoorbeeld een andere camera gebruikt worden als main camera.

```C#
void Update() 
{
	if (Input.GetKeyDown("space"))
            Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
}
```  

Bij bovenstaande code zal elke keer dat op spatie gedrukt worden door alle GameObjecten heen geloopt worden om zo de main camera te vinden. Onderstaande 
code cached deze maincamera om minder last te hebben van deze aanroep.

```C#
Camera mainCam = Camera.main;

void Update() 
{
	if (Input.GetKeyDown("space"))
            Ray ray = mainCam.ScreenPointToRay(Input.mousePosition);
}
```  
[Unity Docs: Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)

