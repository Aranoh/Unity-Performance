# Audio
[terug naar index](/Index.md#unity-settings)  

Een game zonder geluid is natuurlijk niet af. Geluid kan binnen Unity voor best wel wat performance verlies zorgen. Door het goed 
gebruik van import en load settings kan een betere performance gehaald worden, niet alleen doormiddel een betere framerate maar ook zeker met een betere laadt tijd.  

## Actie Punten
* Ken de verschillende Load Type opties en compressie opties
* Gebruik guidelines van muziek en sound effects over importeren en gebruiken audio
##  

### Load Types 

* Compressed In Memory  
Slaat de files op in je RAM maar niet volledig, tijdens spelen word deze gedecompressed en afgespeeld waardoor het ram verbruik tijdelijk verhoogd zal worden.  

* Streaming  
Wat je wil gebruiken als je heel weinig RAM wil gebruiken. Het is iets zwaarder op de CPU maar je krijgt er heel veel memory voor terug.  

* Decompressed On Load  
Slaat de audiofile volledig op in memory. Dit is lichter op de CPU maar kost wel veel memory.

### Compression Types  

Binnen Unity hebben we keuze uit drie verschillende compressie types. In eerste instantie is er PCM, dit is raw audio data. PCM compressed de 
audio niet. PCM is de manier waarop de analoge audio gedigitaliseerd wordt. 

ADPCM is een goedkope manier om audio de encoden en decoden. Vaak gebruiken bij performance gevoelige stukken audio waarbij kwaliteit niet perse 
het belangerijkste is. ADPCM's compressie zal minder bits gebruiken voor dezelfde data waardoor een kleine 'noise' kan onstaan.

Vorbis is het derde gebruikte compressie formaat binnen Unity. Vorbis is een open source compressie systeem met meer audio kwaliteit dan andere 
compressie formaten. Vorbis word veel gebruikt binnen game industrie omdat het niet alleen gratis en open source is maar ook snel werkt en goede 
kwaliteit audio geeft. Vorbis is wat langzamer dan de agressieve ADPCM compressie.

*[Vorbis](https://en.wikipedia.org/wiki/Vorbis)*  
*[PCM](https://en.wikipedia.org/wiki/Pulse-code_modulation)*  
*[ADPCM](https://en.wikipedia.org/wiki/Adaptive_differential_pulse-code_modulation)*  


### Muziek guidelines

Voor muziek op mobile willen we zeker niet de muziek volledig opslaan in memory, een uitzondering kan gemaakt worden voor een game gebazeerd op muziek. Het is voor 
muziek vaak verstandiger om "Streaming" te gebruiken. Hiermee zal het memory verbruik van de muziek drastish minder zijn en dit is beter geschikt voor mobile apparaten. 
Aangeraden is om "Vorbis" compression te gebruiken met deze setting.

Tweede setting die aangeraden word is om de "Compression in memory" te gebruiken. Dit is een beetje de midden weg voor als kwaliteit van de muziek belangerijker wordt. 
Ook hier gebruiken we "Vorbis". Het is mogelijk om de compression quality aan te passen dit gaat dan wel ten kosten van de audio quality, test bij gebruik altijd of 
je audio nog goed klinkt. Richtlijn is 70% compressie.

### Sound Effects guidelines


* Voor **vaak gespeelde** en **korte** geluids effecten gebruik 'Decompress On Load' samen met PCM of ADPCM compressie formaat. Bij gebruik van PCM is decompressie 
niet nodig en je sound effect zal snel geladen zijn. ADPCM gebruikt wel decompressie maar is een stuk sneller dan Vorbis compressie.  
* Voor **vaak gespeelde** en **langere** geluids effecten gebruik 'Compressed In Memory' met ADPCM compressie formaat. ADPCM is zo'n 3.5 keer sneller dan PCM en 
decompressie kost een stuk minder CPU ten opzichte van Vorbis.  
* voor **zelden gespeelde** en **korte** geluids effecten gebruik ook 'Compressed in Memory' met ADPCM.  
* voor **zelden gespeelde** en **langere** geluids effecten gebruik 'Compressed in Memory' met Vorbis formaat. of 'Compressed in Memory' met ADPCM. 
Langere clips zijn niet altijd zo geschikt voor het ADPCM formaat en door het zelden afspelen van deze audio clips is een grotere CPU load vaak niet een heel 
groot probleem. Gebruik Vorbis indien mogelijk.

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/UnitySettings/Culling.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/UnitySettings/Physics.md)