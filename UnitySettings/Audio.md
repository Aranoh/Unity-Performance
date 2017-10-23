# Audio
[terug naar index](/Index.md#unity-settings)  

Een game zonder geluid is natuurlijk niet af. Geluid kan binnen Unity voor best wel wat performance verlies zorgen. Door het goed 
gebruik van import en load settings kan een betere performance gehaald worden, niet alleen doormiddel een betere framerate maar ook zeker met een betere laadt tijd.  

## Actie Punten
* Weet verschillen Load Type opties
* Gebruik guidelines van muziek en sound effects over importeren en gebruiken audio
##  

### Load Types 

* Compressed In Memory  
Slaat de files op in je RAM maar niet volledig, tijdens spelen word deze gedecompressed en afgespeeld waardoor het ram verbruik tijdelijk verhoogd zal worden.  

* Streaming  
Wat je wil gebruiken als je heel weinig RAM wil gebruiken. Het is iets zwaarder op de CPU maar je krijgt er heel veel memory voor terug.  

* Decompressed On Load  
Slaat de audiofile volledig op in memory. Dit is lichter op de CPU maar kost wel veel memory.  

### Muziek guidelines

Voor muziek op mobile willen we zeker niet de muziek volledig opslaan in memory, een uitzondering kan gemaakt worden voor een game gebazeerd op muziek. Het is voor  
muziek vaak verstandiger om "Streaming" te gebruiken. Hiermee zal het memory verbruik van de muziek drastish minder zijn en dit is beter geschikt voor mobile apparaten. 
Aangeraden is om "Vorbis" compression te gebruiken met deze setting.

Tweede setting die aangeraden word is om de "Compression in memory" te gebruiken. Dit is een beetje de midden weg voor als kwaliteit van de muziek belangerijker wordt. 
Ook hier gebruiken we "Vorbis". Het is mogelijk om de compression quality aan te passen dit gaat dan wel ten kosten van de audio quality, test bij gebruik altijd of 
je audio nog goed klinkt.

### Sound Effects guidelines

tekst van het sub onderdeel

* Voor **vaak gespeelde** en **korte** geluids effecten
* Voor **vaak gespeelde** en **langere** geluids effecten
* voor **zelden gespeelde** en **korte** geluids effecten
* voor **zelden gespeelde** en **langere** geluids effecten  
* For frequently played and short Audio Clips use Decompress On Load and PCM or ADPCM Compression Format. When PCM is chosen, no decompression is needed and if audio clip is short it will load very quickly. You can also use ADPCM. It requires decompression, but it is much lighter to decompress than Vorbis.
* For frequently played but medium Audio Clips use Compressed In Memory and ADPCM Compression Format. ADPCM is around 3.5 times smaller than raw PCM and decompression algorithm will not consume as much CPU as Vorbis.
* For rarely played and short Audio Clips use Compressed In Memory and ADPCM. For the same reason as described in point 2.
* For rarely played and medium Audio Clips use Compressed In Memory  and Vorbis Compression Format. This SFX might be too long to be stored using ADPCM and played too rarely, therefore additional CPU power required to decompress wouldn’t be a such pain.  

[![Last Page](https://i.imgur.com/Wr11iwl.png)](/UnitySettings/Culling.md) [![Next Page](https://i.imgur.com/nHLTAf1.png)](/UnitySettings/Physics.md)