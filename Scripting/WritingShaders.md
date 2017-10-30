# Writing Shaders
[terug naar index](/Index.md#scripting)  

Voordat je dit hoofdstuk leest bestudeer eerst de wiki pagina over [Shaders](/Graphics/ShadersPostProcessing.md). Deze wiki pagina gaat wat verder 
in op het schrijven en lezen van shader files zodat hier aanpassingen op gedaan kunnen worden om performance te verbeteren.  

## Actie Punten
* Weet hoe een shader opgebouwd is
* Weet een 'basis' shader te schrijven
##  

### Onderdelen 

Eerste onderwerp en alle tekst die daarbij hoort

#### Sub onderdeel

tekst van het sub onderdeel

```shader
fixed4 fragFunct(v2f IN) : SV_Target
{
	fixed4 col = tex2D(_MainTex, IN.uv);
	return col * _Color;
}
```
---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LevelOfDetail.md)