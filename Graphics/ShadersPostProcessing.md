# Shaders
[terug naar index](/Index.md#graphics)  

Shaders in je game bepalen hoe je 3D objecten eruit komen te zien. Shaders draaien op de video kaart en zullen daardoor los staan van de framerate 
van de rest van je code. Vanuit performance oogpunt is het interessant om te weten welke shaders sneller zijn dan andere en ook waarom.  
## Actie Punten
* Gebruik de goede Rendering Paths
* Gebruik simpele shaders
##  

### Render Paths 

Unity supoort een aantal rendering paths, elk render path heeft zijn eigen kenmerken. Sommige render paths zijn gemaakt voor performance andere 
juist weer om het er extra mooi uit te laten zien.  

In Unity maken wij het meest gebruik van 'Forward Rendering' dit is de meest traditionele 
implementatie voor een render path. Forward rendering kan met een of meerder passes werken en daardoor ook makkelijk aanpasbaar in performance.  

Deffered Shading is een render path gemaakt om goed met licht en shaduw om te kunnen gaan. Deffered rendering is vrij zwaar en ook niet supported op mobile.  

Vertex lit is het laatste render path wat gebruikt kan worden, Vertex lit werkt niet met schaduws en kan ook maar een pass doen voor licht. Vertex 
lit is het simpelste render path dat Unity ondersteunt en daardoor vaak ook de snelste maar door het ontbreken van schaduw zeker niet de mooiste.  

Voor meer informatie over de verschillende features performance kenmerken en supported platforms:  
[Rendering Paths Table](/Graphics/RenderPathsTable.md)  

### Shader performance

Bij forward rendering is de performance afhankelijk van welke shader gebruikt wordt maar ook van het aantal lichtpunten in de scene. Gekeken vanuit 
een performance perspectief zijn er bij forward rendering twee verschillende categorieën shaders, de 'Vertex-Lit' en 'Pixel-Lit' shaders.  

Vertex-Lit shaders in forward rendering zijn altijd goedkoper dan Pixel-Lit shaders. deze shaders werken kijken per vertex welke licht erop valt. 
hierdoor hoeft elke vertex maar een keer getekend te worden.  

Pixel-Lit shaders berekenen op een per pixel basis het licht wat op de pixel valt. Pixel-Lit shaders zullen per licht opnieuw berekend moeten worden. 
Per licht wat gebruikt word zal dus een nieuw render pad doorgelopen worden waardoor je CPU meer tijd kwijt is met commando's sturen naar de video kaart. 
Ook de video kaart zal hierdoor meer werk moeten verichten. 

Pixel-Lit shaders zijn dus meer performance gevoelig maar met Pixel-Lit shaders kunnen wel veel mooie effecten worden gemaakt. (shaduw, normal maps, specular highlights, etc)  

Onthoud dat in Unity per licht aangegeven worden of hij 'important'(pixel lit) of 'niet important'(vertex lit) moet zijn. Een vertex licht wat schijnt 
op een Pixel-Lit shader zal gewoon per vertex of per object berekend worden.

#### Shader complexiteit

Hieronder een lijst van 'Built-in Shaders' beginnend met de meest simpele tot de meest complexe shader. Een complexe shader heeft over het algemeen 
ook een hogere performance cost.

* Unlit  
Gewoon een Texture verder niks eraan toegevoegd.
* VertexLit  
Simpele shader die lichtinval alleen berekend op een per vertex basis.
* Diffuse  
Iets geavanceerder dan VertexLit, kan wel op pixel basis licht inval bepalen.
* Normal mapped  
Iets duurder dan Diffuse, maakt gebruik van normal map en wat andere shader instructies.
* Specular  
Voegt specular highlights toe aan de shader.
* Normal Mapped Specular  
Zelfde als Specular met normal maps, iets duurder dus.
* Parallax Normal mapped  
Voegt parallax normal mapping berekening toe aan de shader.
* Parallax Normal Mapped Specular  
Duurste van allen met parallax normal mapping en specular highlights functionaliteit.

[Unity Docs: Specular](https://docs.unity3d.com/Manual/shader-NormalSpecular.html)  
[Unity Docs: Parralax Diffuse](https://docs.unity3d.com/Manual/shader-NormalParallaxDiffuse.html)  
[Unity Docs: Shader-NormalFamily](https://docs.unity3d.com/Manual/shader-NormalFamily.html)  

#### Mobile shaders

Speciaal voor mobiele platformen heeft Unity een aantal versimpelde shaders gemaakt. Deze shaders hebben niet alle functionaliteit van een niet mobiele shader. 
Zo missen ze bijvoorbeeld specular reflection en per-material kleur support. Om een beter beeld te krijgen van de verschillen tussen standaard en mobiele 
shaders kan gekeken worden in de .shader files zelf. Hier kan bekeken worden waar de shader versimpeld is en hierin is ook gedocumenteerd wat de shader doet.

Meer informatie over het lezen en schrijven van shaders in het hoofdstuk onder scripting [Writing Shaders](/Scripting/WritingShaders.md)  

### Post Processing  

Post processing is de naam gegeven aan full-screen shader effecten die over de image buffer van de camera heen getekend worden voordat ze op 
het scherm weergegeven wordt. Post Processing kan je scene's er heel snel heel mooi uit laten zien. Helaas kunnen deze effecten je wel wat performance 
kosten.  

Gebruik van Post processing zal niet altijd zorgen voor een lagere framerate, dit omdat de GPU los van de CPU kan draaien. Zodra je teveel 
Shaders en Post processing effecten zal gebruiken zal je gaan merken in b.v. je profiler dat je op je video kaart moet wachten elke frame. We noemen dit 
'GPU Bound'. Om te voorkomen dat Post processing mee gaat tellen met performance is het goed om te weten hoeveel effect verschillende effecten 
hebben op de performance van je spel.

Hier een link naar geteste framerate verlies van verschillende post processing effecten:  
[Post processing effects table](/Graphics/PostProcessingTable.md)  

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Graphics/LowDetailCamera.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/Overdraw.md)