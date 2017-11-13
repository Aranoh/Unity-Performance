# Physics
[terug naar index](/Index.md#unity-settings)  

Physics in een game zijn vaak vrij belangerijk. Het kan soms gebeuren dat een game teveel physics objecten heeft om goed te kunnen draaien. 
Mocht dit het geval zijn kunnen wat slimme dingen gedaan worden om de performance van je game te verbeteren en te zorgen dat je framerate 
niet afhankelijk is van je physics objecten. 

Denk eraan altijd 2D te gebruiken als dit mogelijk is. Gebruik van 3D voor een 2D game voegt een 
extra demensie toe waar je niks mee kan.  

## Actie Punten
* Time manager gebruiken om de tijd gespendeerd aan physics te verkleinen
* Weet welke colliders minder goed performen en vermijd gebruik hiervan
* Gebruik collision matrix om aantal collisions te verkleinen en performance hierdoor te verbeteren
* Maak zuinig gebruik van Raycasting
* Gebruik rigidbody voor bewegende objecten
##  

### Time manager  

De time manager heeft instellingen voor FixedUpdate en physics, Binnen de time manger istellingen (die te vinden zijn onder 'Edit>project settings>Time') 
zijn er twee opties die de performance van je game kunnen verbeteren door niet zoveel tijd bezig te zijn met physics.

Time manager opties:  
* Fixed Timestep  
Fixed timestep is de interval van FixedUpdate en Physics berekeningen. Door dit te verhogen word het interval waarop deze functionaliteit aangeroepen 
wordt vergroot. Probeer een setting te vinden die geen effect heeft op je spel (genoeg precisie behouden voor physics berekeningen) maar wel voor
een betere performance kan zorgen.  

* Maximum Allowed Timestep  
Deze inselling kan gebruikt worden om spikes in je game te verminderen door de maximale tijd die physics berekeningen kunnen duren te limiteren 
door deze inselling goed te gebruiken kan ervoor gezorgd worden dat je nooit tegen onverwachte framerate problemen aan zal lopen door physics.  

Het is altijd nuttig om voordat je met deze instellingen gaat spelen je eerst gaat kijken of je niet gewoon teveel physics objecten aan het gebruiken 
bent. In de internal profiler kan bekeken worden hoeveel physics objecten in je huidige scene gebruikt worden.  

### Colliders  

Colliders binnen Unity komen in veel verschillende vormen. Niet elke collider is even 'snel' als het op performance neerkomt. Een goed voorbeeld 
van een minder snell collider is de mesh collider. Deze collider heeft een vrij hoge invloed op de performance van je game en het is dan ook verstandig 
om het gebruik van deze collider te beperken. Probeer mesh colliders om te zetten naar primitieve vormen die lijken op het gemodeleerde object. Dit is 
natuurlijk niet bij alle objecten mogelijk maar voor dingen als gebouwen en andere objecten voor de omgeving is dit zeker een goede optie.  

Een tweede collider die veel performance kan kosten is het gebruik van wheel colliders. Gebruik deze colliders dan ook alleen wanneer dit echt nodig is.  

#### Collision matrix  

Om de inpact van colliders en collisions te verkleinen kan gebruik gemaakt worden van de 'Collision Matrix' Met de collision matrix kan ingesteld 
worden welke objecten wel en niet met elkaar colliden. Dit word gedaan in de physics engine zelf en zal dus geen performance van je unity afhalen. 
Door gebruik van deze collision matrix kan het aantal onnodige collisions verkleint worden.  

### Raycasting  

Raycasting is een vrij zware physics operatie. Gebruik raycasts dus op een goede en zuinige manier zodat dit niet ten kosten hoeft te gaan van de performance 
van je game. Om te zorgen dat racasting niet een probleem gaat worden zijn hier wat pointers waarop gelet kan worden.

* Gebruik zo min mogelijk raycasts  
Dit klinkt misschien een beetje voordehand liggend maar probeer zo min mogelijk raycasts te gebruiken om het gewenste resultaat te krijgen.  

* Gebruik niet te lange raycasts  
De performance van een raycast is direct afhankelijk van de lenge van de ray. Gebruik dus niet te lange raycasts waardoor de performance omlaag zal gaan.  

* Gebruik bij voorkeur geen mesh colliders voor racasting  
Mesh colliders zoals hierboven ook beschreven hebben een hogere impact op de performance dit geld niet alleen voor collisions maar ook van raycasts naar een mesh collider.  

* Gebruik raycasts niet in Update functies  
Vaak is het overkill om een raycast in een Update of FixedUpdate te plaatsen. Probeer dit niet te doen als het niet nodig is.  

* Gebruik maken van layer masks  
Gebruik de layer masks binnen raycasts om onnodige berekeningen van de raycast te veminderen en zo betere performance te krijgen.  

### Rigidbody en static colliders  

Voor physics objecten binnen unity woren rigidbody componenten gebruikt. Zelfs als gewerkt word met statische objecten of triggers moet gebruik 
gemaakt worden van dezer rigidbody's.  

Een game object wat geen rigidbody heeft word gezien als statische collider. Let erop dat een statishe collider niet verplaatst wordt. Verplaatsen 
van zo een collider zal ervoor zorgend at de gehele fisieke wereld binnen de game opnieuw berekend zal moeten worden. Gebruik voor bewegende objecten 
dus altijd rigidbody colliders.  

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/Audio.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/LightAndShadows.md)