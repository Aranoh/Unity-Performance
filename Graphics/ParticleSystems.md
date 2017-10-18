# Onderwerp
[terug naar index](/Index.md)  

Een kort inleidend stukje over het onderwerp

## Actie Punten
* eerste_actie_puntje
* punt_twee_staat_hier
##  


### Performance Modules

Binnen particle systems heb je een hele set verschillende modules die ieder iets anders doen met hoe het particle systeem eruit ziet. Deze verschillende systemen 
hebben ook allen hun eigen performance kenmerken. niet elk systeem is even snel als een ander systeem.

Om een beeld te krijgen van hoe de verschillende systemen invloed hebben op de performance van je game staan hier onder wat grafieken.

![Module Performance](https://i.imgur.com/xw1EvI7.png)  
![MinMaxCurve](https://i.imgur.com/JKz5J38.png)  
![MinMaxGradient](https://i.imgur.com/A76XHqL.png)  
![Shape Module](https://i.imgur.com/FHnn7yR.png)  


#### extra informatie
Bovenstaande grafieken komen uit een demonstratie van de nieuwe particle systemen van Unity 2017, om een beter beeld te krijgen van wat de verschillende systemen
voor mogelijkheden hebben raad ik aan een keer te kijken naar dit demo project of presentatie.

[![Video](https://i.imgur.com/9r1oczW.png)](https://www.youtube.com/watch?v=_N4iL0SQ9q8)  

[Download project](http://bit.ly/2ueFDWF)  

start + stop itterate door alle children in particle system hierarchie. Om hierin alle particle Systems uit te zetten. als dit niet nodig is gebruik de 'with children' parameter
mocht het toch nodig zijn cache dan alle children die particle systems hebben en gebruik alsnog 'withChildren: false' 

Pas op met constant aanroepen van "Stop" en "Start" zal memory allocaten, ookal is het particle system al gestopt

### Particle system culling

zeker mogelijk, support toegevoegd in nieuwe versies van unity. ruig om te doen: link naar culling pagina

### Module's performance

Tabellen laten zien van hoe snel alle verschillende module's zijn
conclusie trekken met deze tabellen

---
[![Last Page](https://i.imgur.com/Wr11iwl.png)](/Graphics/Polycount.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/UnitySettings/DrawCallsBatching)