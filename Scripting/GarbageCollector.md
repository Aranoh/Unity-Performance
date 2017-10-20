# Garbage Collecor
[terug naar index](/Index.md#scripting)  

Door het draaien van je spel zal steeds meer data in je memory opgeslagen worden. De garbage collector speelt hier op in door om de zoveel tijd een keer heel 
je memory door te lezen en alle niet gebruikte data weer vrij te maken voor gebruik. Dit gaat uiteraard niet zonder kosten en daarom is het verstandig om 
zo min mogelijk "data te alloceren" tijdens het draaien van je spel. Hoe minder de garbage collector hoeft te draaien hoe minder performance het je kost bij je game.  

## Actie Punten
* Weten verschil 'Stack' en 'Heap' memory en welke waardes waarin komen
* Cashing data om niet elke frame memory te hoeven alloceren
* Zuinig omgaan met gebruik garbage makende methode's
* Draai 'dure' code niet elke frame maar op een timer
* Hergebruiken van collecties
* Gebruik Stringbuilder in de plaats van String voor minder garbage
* Let op bij Unity API calls die garbage maken
* 'Boxing' van waardes creëert garbage, let op bij gebruik
* Voorkom aanmaken van garbage bij yields in coroutines
##  

### Heap VS Stack 

Binnen Unity worden twee verschillende soorten memory gebruikt. Elke variabele die aangemaakt wordt zal op een van deze twee 'pools' terecht komen. Welke pool 
gebruikt wordt hangt af van wat voor soort object er in het memory geplaatst is.  
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
* Wanneer dit zelf gedaan word vanuit code

Aanroepen garbage collector:
```c#
System.GC.Collect();
```
[MSDN: GC.Collect](https://msdn.microsoft.com/en-us/library/xe0c2357(v=vs.110).aspx)

Het is wel zo dat memory op de heap door veel alloceren en dealloceren van memory 'fragmented' raakt, dit wil zeggen dat er lege stukken in je heap zullen vallen 
die niet zo makkelijk meer gebruikt kunnen worden. Dit is een goede reden om goed op te letten op je memory allocatie om dit te voorkomen.


#### Value typed VS Reference typed

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
* b.v. Vector3 of Quaternion
<br><br>
</div>  

Code voorbeeld:
```C#
	//Value type variable (changing pos does not change transofrm.position)
	Vector3 pos = transform.position;
	pos = new Vector3(0, 2, 0);
	
	//Reference type variable (changing tran will change transform.position)
	Transform tran = transform;
	tran.position = new Vector3(0, 2, 0);
```  
<div>  <br> </div>

## Optimaliseren garbage collector

Voor we beginnen met optimaliseren moeten we eerst weten waar we dit kunnen doen. Voor de garbage collector is het aan te raden om de profiler goed te 
gebruiken, met de profiler kan je precies zien waar 'gc alloc' gedaan wordt.

Een beter framerate is te halen als:
* De tijd die de garbage collector nodig heeft om op te schonen verkleind wordt
* Het interval waarop de garbage collector draait vergroten
* De garbage collector draaien op handige tijden waneer het geen performance kost   

Dit brengt ons meteen op drie strategien om het te verbeteren:
* Organiseer je code zo dat er minder objecten in de heap memory gezet worden. Minder objecten betekend automatish een snellere garbage collection
* Verminder het aantal allocaties en deallocaties op 'performance-critical' tijden, wanneer er weinig gealloceerd word zal ook de garbage collector niet getriggerd worden
* Draai de garbage collector zelf at runtime op rustige tijden wanneer je framerate er niet onder zal leiden

De kopjes hieronder gaan dieper in hoe je de garbage allocatie kan verkleinen door het toepassen van 'best practices' tijdens coderen.

### Cashing

Door het slim cashen van waardes kan memory direct hergebruikt worden en hoeft het niet eerst gedealloceerd te worden om het vervolgens weer te alloceren.

Het volgende voorbeeld laat een stuk code zien waarin garbage gecreëerd word door het aanmaken en vullen van een nieuwe array

```C#
void OnTriggerEnter(Collider other)
{
	Renderer[] allRenderers = FindObjectsOfType<Renderer>();
	ExampleFunction(allRenderers);
}
```
Onderstaand stukje code cashed deze array zodat deze constant opnieuw aangeroepen kan worden. Er word in dit geval maar een keer garbage gemaakt en niet 
bij elke aanroep van 'OnTriggerEnter'  

```C#
private Renderer[] allRenderers;

void Start()
{
	allRenderers = FindObjectsOfType<Renderer>();
}

void OnTriggerEnter(Collider other)
{
	ExampleFunction(allRenderers);
}
```
### Alloceren in update

Het is niet aan te raden om in een update loop een allocerende functie te hebben, aangezien deze elke frame aangeroepen wordt zal garbage snel oplopen en 
moet de garbage collector veel werk verrichten om deze leeg te houden. Een techniek die toegepast kan worden is om de functie in update alleen uit te voeren 
als de waardes ook echt veranderd zijn.

#### Code draaien op veranderingen

Onderstaand voorbeeld laat zien dat een functie elke frame aangeroepen word met als argument de x positie van dit object.

```C#
void Update()
{
	ExampleGarbageGeneratingFunction(transform.position.x);
}
```

Bovenstaande funcie zal elke frame garbage creëren. Om dit te voorkomen is de functie herschreven om alleen een aanroep de doen op de garbage creërende funcie 
als er iets veranderd is in de x positie van het object.
```C#
private float previousTransformPositionX;

void Update()
{
	float transformPositionX = transform.position.x;
	if (transformPositionX != previousTransformPositionX)
	{
		ExampleGarbageGeneratingFunction(transformPositionX);
		previousTransformPositionX = transformPositionX;
	}
}
```

#### Code draaien op een timer

Een andere techniek die gebruikt kan worden is om in plaats van te kijken naar veranderingen je stuk code niet elke frame aan te roepen. misschien is 60 aanroepen 
per seconde voor je object veel te veel en kan er genoegen worden genomen met bijvoorbeeld een aanroep per seconde. Door op een slimme manier na te denken over 
hoe vaak je code moet draaien om precies genoeg te zijn kan een hoop garbage allocatie tegen gegaan worden.

### Hergebruiken van collecties

Het constant aanmaken van een nieuwe collectie kan al snel voor veel garbage zorgen in je game. Het is daarom verstandig om beter om te gaan met verschillende 
collecties. Hergebruik waar mogelijk dezelfde list of array om er opnieuw objecten in te stoppen, dit is een stuk zuiniger dan constant nieuwe lists of arrays 
aanmaken.

Onderstaand stuk code laat zien hoe het niet moet
```C#
void Update()
{
	List myList = new List();
	PopulateList(myList);
}
```
door de 'Clear' functie aan te roepen op de van te voren aangemaakte lijst word er een stuk minder garbage gemaakt in dit stuk code
```C#
private List myList = new List();
void Update()
{
	myList.Clear();
	PopulateList(myList);
}
```
### Object pooling
Game objecten zijn refrence types, het aanmaken van een GameObject zal dus direct invloed hebben op de heap memory. Object Pooling kan gebruikt worden om 
ervoor te zorgen dat er at runtime geen garbage meer gemaakt kan worden door het spawnen en despawnen van game objecten, objecten kunnen dan namelijk uit 
de al bestaande pool gehaald worden in plaats van te instantiëren. 

voor meer info over pooling zie het hoofdstuk over [Pooling](/Scripting/Pooling.md).

### Strings creëren garbage

Strings zijn immutable, dat wil zeggen dat ze na aanmaken niet meer veranderd kunnen worden. Het 'veranderen' van een string spreekt een nieuw stuk memory aan op 
de heap memory. Hierdoor kan het veel aanpassen van strings snel voor best wel wat garbage zorgen.

Om dit tegen te gaan maken we gebruik van de zogeheten 'stringbuilder' een stringbuilder kan je toepassen om veel aanpassingen te doen op een string of om verschillende strings 
aan elkaar toe te voegen, hieronder wat voorbeelden.
```C#
string test = "foo";
void Update()
{
	test += "bar";
	test = "foo";
}
```
Hierboven zal bij het aanmaken van de string "foo" memory gealloceerd worden, maar ook bij het toevoegen van "bar" aan deze string en bij het terug veranderen naar 
"foo" zal memory alloceren, al deze memory word als garbage gezien.

Door gebruik van stringbuilder kan een hoop minder garbage gemaakt worden.
```C#
StringBuilder strBuilder1 = new StringBuilder("foo", 8);
void Update()
{
	strBuilder1.Append("bar");
	strBuilder1.Remove(0, 8);
	strBuilder1.Append("foo"); 
}
```
bovenstaande methode zal alleen memory alloceren bij het opvragen van de string van de stringbuilder, dit gebeurd met 'toString()' waarbij een string object 
gemaakt word (dus ook memory gebruikt) wel zal gedurende de update loop geen extra memory gealloceerd worden.

[MSDN: StringBuilder](https://msdn.microsoft.com/en-us/library/system.text.stringbuilder(v=vs.110).aspx)

### Unity API calls

Er zijn heel wat Unity API calls die garbage creëren, een completer overzicht over mogelijkheden en struikelblokken is te vinden op de wiki pagina over 
[Unity API calls](/Scripting/UnityApiCalls.md).

### Boxing

Boxing is een term die gebruikt word voor het verwerken van een 'value type' om een 'reference type' te vullen met data. Er zijn hier niet direct alternatieven 
voor maar wel word afgeraden om deze te gebruiken als performance een probleem lijkt te worden.

Hieronder een simpel voorbeeld van 'boxing'.

```C#
void ExampleFunction()
{
    int cost = 5;
    string displayString = String.Format("Price: {0} gold", cost);
}
```

in dit voorbeeld word 'cost' gebruikt om de string 'displayString' op te bouwen, hierdoor word er memory tijdelijk gealloceerd om het cost object weg te zetten. 

```C#
int i = 123; 
// The following line boxes i. 
object o = i; 
```
Een ander simpel voorbeeld van 'boxing' hierin word een 'object' field gebruik voor het bijhouden van een simpele int waarde. Deze int waarde zou geboxt moeten 
worden en dus creëert dit garbage.  


### Coroutine yields

Gebruik maken van coroutines maakt in eerste instantie al garbage, deze coroutines worden namenlijk in het memory weg gezet. Dit is onvermeidelijk maar met 
normaal gebruik van coroutines zou dit nooit een probleem moeten zijn. Wel kan binnen een coroutine garbage gemaakt worden, met name met de yield functie. 

Dit voorkomen is vrij eenvoudig, let op met welke waardes je returned en creëer van te voren return value's die je meerdere keren kan teruggeven.

```C#
public IEnumerator gameLogic()
{
	while (!isComplete)
	{
		yield return new WaitForEndOfFrame();
		yield return 0;
	}
}
```
Bovenstaande code creëert elke frame garbage, zowel voor het maken van een nieuwe 'WaitForEndOfFrame' als bij het teruggeven van een int waarde nul 
die geboxt moet worden binnen de return. Onderstaand code blok laat zien hoe dit beter kan door van te voren een 'frame' object aan te maken en 
null terug te geven i.p.v. int waarde nul. 

```C#
public IEnumerator gameLogic()
{
	WaitForEndOfFrame frame = new WaitForEndOfFrame(); 
	while (!isComplete)
	{
		yield return frame
		yield return null;
	}
}
```


---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/Pooling.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/Graphics/LevelOfDetail.md)