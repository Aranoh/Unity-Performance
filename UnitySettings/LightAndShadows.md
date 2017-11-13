# Onderwerp
[terug naar index](/Index.md#unity-settings)  

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

Belangerijke instellingen in het eerste gedeelte zijn:
* Ambient Mode
keuze uit twee opties, 'Realtime' en 'baked' kies als je gebakken data wil gebruiken voor ambient licht voor de 'baked' optie.
* 
### Light probes

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/Physics.md)