# Unity UI
[terug naar index](/Index.md)  

Unity UI is niet het zuinigste systeem wat draait binnen Unity, al snel kan veel framerate verloren gaan door verkeerd gebruik van Unity UI.Hieronder heb ik een aantal guidelines 
staan voor het gebruik van Unity UI. Aangeraden word deze guidelines zo goed mogelijk te volgen bij het maken van een UI zodat er geen framedrops hoeven komen vanwege Unity UI.  

## Actie Punten
* Gebruik los canvas voor static and dynamic objecten
* Graphic raycasters niet gebruiken wanneer niet nodig
* Let op render/event camera in te stellen
* Gebruik Anchors in plaats van Layout groepen
* Slim objecten poolen door disablen elementen voor reparenting
* Ga slim om met tekst elementen, veranderende tekst kan best zwaar zijn
* Gebruik op een slimme manier Dynamic fonts met fallback font en zonder Best Fit
* Scroll view pooling voor betere performance
##  

### Use Multiple canvases  

Unity UI maakt in eerste instantie gebruik van canvases, dit zijn verzamel objecten van UI onderdelen. Een nadeel van gebruik van deze canvases is dat 
wanneer een van de objecten op zo'n canvas verandert het alle andere objecten op dat canvas laat "rebuilden". Dit wil zeggen dat elk object op de canvas 
zijn layout opnieuw berekent, zijn meshes opnieuw genereert en material's worden opnieuw gegenereerd vanwege batching.

Het splitsen van je UI elementen in minstens 2 canvases is een goed startpunt hiervoor. zo heb je er een met alle static objecten en een met dynamic objecten. 
met het veranderen van een object op het ene canvas blijft je andere canvas gewoon onaangetast. dit zorgd ervoor dat dit deel van je canvas niet opnieuw hoeft te rebuilden.  

Met het gebruik van meerdere canvases kan wel gebruik gemaakt worden van een 'nested canvas' zo een canvas neemt de render mode van zijn parent over waardoor 
je dus geen problemen hoeft te krijgen met uitlijnen van je verschillende canvases.  

### Graphic Raycaster

Een graphic raycaster wordt gebruikt om screen/touch input te regelen op je canvas, dit object is bedoeld om input mogelijk te maken op verschillende UI elementen. 
Een graphic raycaster zit standaard op elk UI onderdeel dat Unity gebruikt. Dit is echter overbodig en zorgd op zijn beurt ook weer voor performance loss. Dit 
aangezien bij elke druk/klik op het scherm al deze raycasters gechecked worden is het verstandig deze uit te zetten op objecten die geen input nodig hebben.    

### Render en event camera 

Op een canvas word van je verwacht dat je een camera insteld ofwel als render camera voor screen space canvases of als event camera voor world space canvases.  

Aan te raden is hier altijd een camera in te stellen. Wanneer dit niet gedaan word zal unity zelf naar de Camera.main vragen om deze te gebruiken, soms wel meerdere 
keren per frame.  

Waarom gebruik van Camera.main zo traag is kan je terug te vinden op de _[UnityApiCalls](/Scripting/UnityApiCalls.md)_ pagina onder het kopje "Caching Unity Objects".  

### Layout Groups  

Layout groepen zitten met ongeveer hetzelfde probleem als canvases door het veranderen van een object in een Layout groep word heel het layout system doorgezocht 
met 'GetComponent' calls dit maakt het gebruiken van meerdere nested Layout objecten niet echt performance gericht. Probeer dus ook zo min mogelijk gebruik te maken 
van deze layout groepen. Mocht je toch graag gebruik willen maken van schalende dingen op je scherm, maak dan slim gebruik van 'Anchor points', hiermee kan veel 
van de funcionaliteit van layout groepen goed nagedaan worden.

### UI Object pooling  

Object pooling kan bij UI net als bij 3D games best wel wat performance schelen. Voor bijvoorbeeld het gebruik van scroll lists in je inventory scherm of voor terugkomende UI objecten in een 
2D game is het mogelijk om object pooling te gebruiken. Object pooling werkt in UI hetzelfde als met 3D objecten.  

Om ervoor te zorgen dat je zo min mogelijk objecten "dirty" maakt is het aan te raden om eerst een object te disablen voordat je het gaat verplaatsen in de hiërarchie 
Dit zorgt ervoor dat alleen het oude parent object "dirty" wordt en het nieuwe object wordt pas "dirty" als je het verplaatste object enabled.
Ook is het verstandig om eerst alle waardes te veranderen van het object voordat je het enabled. Ook dit zorgt voor minder "dirty" maken van het nieuwe canvas.

Voor meer info over object pooling bekijk de wiki pagina over [Pooling](/UnityApiCalls.md#garbage-creating-api-calls).  

### Uitzetten Canvas Renderer  

Een trucje dat gedaan kan worden is om verdwijnende UI elementen op een los canvas te zetten en van dit canvas alleen de Canvas renderer te disablen. 
Op deze manier voorkom je dat heel het canvas laat rebuilden. Let wel op dat deze componenten op dat canvas dan nog wel gezien kunnen worden door de graphic 
raycaster en dat MonoBehaviours op het object nog zullen doorgaan.  

### UI Text

Het gebruik van tekst komt niet altijd zonder performance verlies. Het grote probleem van tekst is dat het uit heel veel 'quads' bestaat en in deze quads zit ook veel 
leegte. Deze quads kunnen er zelfs voor zorgen dat je de batching van andere UI objecten kapot gaat omdat ze toevallig in een rare positie staan. 

UI Text gebruikt per karakter een quad, het veranderen van tekst zorgt ervoor dat al deze quads opnieuw berekent moeten worden. Ook het aan en uitzetten van 
het text object of een van zijn parents zorgt voor het zelfde gedrag.  

#### Dynamic fonts

Het tekenen van fonts gaat in Unity via een texture atlas. In deze atlas zitten alle fonts die op het moment weergeven worden. Voor elke variant van een font 
word een glyph aangemaakt binnen dit atlas, dit wil zeggen dat Arial en Arial Bold hun eigen plek krijgen op dit atlas, dit is ook waar voor alle verschillende 
groote van dit font. Het is verstandig zuinig aan te doen met het constant scalen en veranderen van een font om performance te verbeteren. Als een font een 
waarde tegen komt dat nog niet in de atlas staat word heel de atlas opnieuw gebouwd. 

Het is mogelijk om met gebruik van dynamische fonts van te voren aan te geven welke fonts in de texture atlas moeten komen, dit kan handig zijn voor als je veel 
teksten wilt gaan veranderen door van te voren deze fonts al in de texture te zetten. Dit gebeurd door aanroep van "RequestCharactersInTexture" te doen en hier 
de string van karakter die je gaat gebruiken aan mee te sturen.

Een ander voorbeeld waarvoor dit gebruikt kan worden is als je van te voren zeker weet dat je bijvoorbeeld alleen nummers gaat gebruiken. Je kan deze nummers dan 
in de texture zetten voor gebruik zodat dit niet meer at runtime hoeft te gebeuren.

Code voorbeeld van "RequestCharactersInTexture" is te vinden in de [Unity Docs: Font.RequestCharactersInTexture](https://docs.unity3d.com/ScriptReference/Font.RequestCharactersInTexture.html)  

Een belangerijke highlight uit de code:

```C#
 void Update()
{
	string str = "Hello World";
	
	// Keep requesting our characters each frame, so Unity will make sure that 
	// they stay in the font when regenerating the font texture.
	font.RequestCharactersInTexture(str);
}
```

[Unity Docs: Font.RequestCharactersInTexture](https://docs.unity3d.com/ScriptReference/Font.RequestCharactersInTexture.html)  

##### Best Fit

Best fit bij een tekstfield en font zorgt ervoor dat Unity altijd de grootst mogelijke font size gebruikt wat past binnen de tekst boxen waar dit font in gebruikt 
wordt. Dit is niet helemaal effectief en kan ervoor zorgen dat je font atlas snel zal groeien. Om dit te voorkomen en een betere prestatie te krijgen is 
aan te raden 'best fit' niet zomaar te gebruiken. 

Werk je met unity 5.3 of lager dan is het helemaal af te raden er gebruik van te maken. Vanaf unity 5.4 is 'best fit' aanzienlijk verbeterd maar het zal altijd 
trager zijn dan gebruik maken van static fonts. Hoe meer tekst gebruikt maakt van 'best fit' hoe groter het performance probleem zal worden.

### Scroll View

Scroll views in unity kunnen al snel voor performance issue's zorgen door de grote hoeveelheden objecten die vaak gebruikt worden in een scrollview. We hebben 
twee oplossingen om de elementen van het scrollview op het scherm te weergeven.

* Scrollview vullen met alle elementen die nodig zijn de content te weergeven.
* Pooling gebruiken en elementen verplaatsen wanneer nodig om de content te weergeven.

Voor een simpel klein scrollview kan de eerste optie gebruikt worden. Het nadeel is dat buiten een lange instantiatie tijd ook een lange 'rebuild' tijd voor nodig 
is. Hierboven heb je kunnen lezen dat een verandering in een ander UI element ervoor kan zorgen dat dit scrollview zijn content ook moet rebuilden. Gebruik deze 
methode alleen voor simpele scrollviews met bijvoorbeeld alleen een paar tekst elementen hierin.

Tweede methode is niet eenvoudig te implementeren maar voor een complex scrollview vaak wel noodzakelijk.

RectMask2D component kan gebruikt worden om ervoor te zorgen dat elementen buiten het scroll view geen drawcalls gebruiken.

[Unity Docs: RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html)

##### position-based scroll view pooling

Aangezien reparenting van UI elementen aan een canvas ervoor zorgd dat heel het canvas opnieuw opgebouwd moet worden is de standaard pooling oplossing in scrollviews 
niet de beste om te kiezen kwa performance. Aangeraden word om een speciaal pool systeem te bouwen gebazeerd op het verplaatsen van UI objecten die nodig zijn 
binnen het scrollview. Je kan dit doen door een custom implementatie te maken van het scrollview of layout systeem. 

---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Scripting/Datastructures.md)[![Next Page](https://i.imgur.com/nHLTAf1.png)](/Scripting/Pooling.md)