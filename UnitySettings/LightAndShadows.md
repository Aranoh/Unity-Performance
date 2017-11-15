# Licht en Shaduws
[terug naar index](/Index.md#unity-settings)  

/Afbeeldingen/

Realtime licht in een game kan behoorlijk veel power eisen van je device. Toch ziet een game er met licht en schaduw er een stuk mooier uit 
dan een game zonder licht. Om licht te kunnen krijgen in je game en toch goede performance te hebben kan gebruik gemaakt worden van Unity's 
'light baking' systeem.  

## Actie Punten
* Weet de voor en nadelen van light baking
* Weet hoe lightbaking werkt binnen Unity scenes
* Weet gebruik te maken van light probes
##  

### Baked light voor en nadelen 

Door gebruik van light baking zal je game met meer framerate kunnen draaien. Een nadeel van light baking is wel dat je meer memory kwijt bent voor 
het opslaan van gebakken data. Het is dus een kwestie van CPU load omzetten naar memory verbruik.

Het grootste nadeel van light baking is dat je geen dynamishe schaduws meer kan hebben. De enige manier waarop dit nog wel kan is door een 'mixed' 
licht modus te gebruiken. Met mixed mode kan licht gebakken worden maar kan er ook een deel 'realtime' licht zijn voor dynamishe objecten. Het nadeel 
is dan wel dat je een hoop van je gewonnen performance voor renderen weer kwijt bent omdat je toch realtime licht berekeningen moet doen.

Met mixed lightning mode zullen alleen statishe schaduwen en global illumination gebakken worden. Direct lichtinval zal realtime berekend worden.  

### Light baking Unity

Light baking in Unity gaat voor het grootste gedeelte via het 'Lighting' window. Dit window is terug te vinden via 'Window > Lighting > Settings'.  

In dit window zijn een aantal opties terug te vinden. In eerste instantie zijn er opties voor de normale licht instellingen. Er zijn instellingen 
voor gebruik van skybox of sky color en reflecties.  

Belangerijke instelling uit het eerste gedeelte:  
* Ambient Mode  
keuze uit twee opties, 'Realtime' en 'baked' kies als je gebakken data wil gebruiken voor ambient licht kies dan voor de 'baked' optie.

Realtime Lighting:   
* Realtime Global Illumination  
Wanneer deze checkbox aangevinkt is zal 'Global Illumination' realtime berekend worden.

Mixed Lighting:   
* Baked Global Illumination  
Geeft aan of mixed en baked lichten gebruik maken van de gebakken data.  

* Lighting Mode  
Beslist hoe mixed lights en shaduwen werken in je scene. Om een beter beeld te krijgen van welke opties er allemaal zijn en of ze wel of niet gebruik 
maken van gebakken data kan je de [Lighting Modes Reference Card](/UnitySettings/LightingModesCard.md) bekijken.  

#### Stappen plan Light baking  

Stap één begint heel simpel. Sla je scene op! Zonder opgeslagen scene kan Unity namelijk niet zijn light baking doen. Je hoeft niet perse elke verandering op te slaan 
voordat je kan bakken maar er moet op zijn minst een opgeslagen file zijn van de huidige scene.  

Voordat we beginnen met instellingen goed zetten gaan we eerst het automatish licht bakken uitzetten. Dit kunnen we doen via het 'lighting window' 
dit window is te vinden via 'Window' > 'Lighting' > 'Settings', helemaal onderaan in het eerste of tweede tabje zorg dat 'Auto Generate' uit staat. 
Je mag deze optie aanzetten maar het geeft een betere workflow om te kunnen builden wanneer we helemaal klaar zijn. Zo kunnen we spelen met de 
settings en op 'Generate Lighting' drukken wanneer we klaar zijn.  

![LichtShaduw_AutoGenerate](/Afbeeldingen/LichtShaduw_AutoGenerate.png)  

Bedenk eerst wat je wilt doen met het light baking systeem. Deze guide gaat ervanuit dat het systeem gebruikt wordt voor het bakken van een statishe 
omgeving. We gebruiken hierbij Light probes voor dynamishe objecten, dynamishe objecten zullen geen schaduw geven. gebruik 'Mixed' licht om schaduw 
te krijgen van dynamishe objecten. Hierdoor verlies je wel veel van je lightbaking performance winst.

Eerste stap voor het lightbaking systeem is om voor alle licht objecten uit de scene de 'Mode' op 'baked' te zetten. Dit zorgd in eerste instantie 
niet voor veranderingen maar zal bij bakken deze lichten mee nemen en na het berekenen van de lightmap zal hij dit licht uitzetten.  

![LichtShaduw_BakedMode](/Afbeeldingen/LichtShaduw_BakedMode.png)  

Hierna gaan we al onze objecten af waar licht op kan vallen. We gaan checken of alle statishe objecten ook echt op 'static' staan. Het op static 
zetten van je game objecten zorgd ervoor dat deze mee genomen worden in het static lightmapping process. 

![LichShaduw_StaticObjects](/Afbeeldingen/LichShaduw_StaticObjects.png)  

Nadat wij alle objecten goed hebben gezet om te bakken kijken we nog even naar de settings in het 'Lighting window'. In dit window vinden wij het kopje 'Lightmapping Settings' 
terug. Hieronder staan wat opties die de presisie van de lightmap veranderen. Deze settings beinvloeden hoe de lightmap eruit komt te zien later. Maar ook kan met 
veranderen van deze settings de baktijd verhoogd worden. Het is niet verkeerd om te beginnen met 'lage' settings en deze pas richting release aan te passen voor 
een beter uitziende lightbake.  

![LichtShaduw_LightmappingSettings](/Afbeeldingen/LichtShaduw_LightmappingSettings.png)  

* Lightmapper  
Welk systeem gebruikt moet worden. Enlighten is Unity's oude systeem progressive het nieuwe. Progressive zal enlighten overnemen in de toekomst voor nu zijn ze allebij nog 
te gebruiken.  

* Indirect/Lightmap Resolution  
Geven aan hoe presies de lightmap moet worden. hoe hoger de resolutie hoe betere textures er gemaakt worden voor de lightmap. Aan te raden is dit pas omhoog te zetten 
wanneer je richting een release verzie komt om baktijd kort te houden.  

Met al deze instellingen kan gespeeld worden tot het gewenste resultaat behaald is.

Wanneer al je objecten en instellingen goed staan kan je op 'Generate Lightning' klikken in het lighting settings scherm. Unity zal dan het light baking process starten
en de lightmaps aanmaken. Nadat het process klaar is zal je in je scene view meteen het resultaat kunnen zien.  

Mocht het bakken niet goed gaan probeer dan een keer de oude lightmap data weg te gooien met het dropdown menu onder 'Generate Lighting'.

#### Light probes

Light probes toevoegen in scene
altijd boven terrain (anders zwarte objecten)
BAKKEN
---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/Physics.md)