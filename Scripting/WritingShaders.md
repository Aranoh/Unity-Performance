# Writing Shaders
[terug naar index](/Index.md#scripting)  

Voordat je dit hoofdstuk leest bestudeer eerst de wiki pagina over [Shaders](/Graphics/ShadersPostProcessing.md). Deze wiki pagina gaat wat verder 
in op het schrijven en lezen van shader files zodat hier aanpassingen op gedaan kunnen worden om performance te verbeteren.  

## Actie Punten
* Weet hoe een shader opgebouwd is
* Weet een 'basis' shader te schrijven
##  

### Shader Componenten 

Shaders binnen Unity worden geschreven in een .shader file. Visual studio heeft standaard geen intelliSense support voor .shader files, deze zullen 
we moeten downloaden. Gelukkig zijn hier wat plugins voor te vinden op het internet.  

Ik maak zelf gebruik van [ShaderLabVS](https://forum.unity.com/threads/free-shaderlabvs-visual-studio-extension-for-unity-shaderlab-programming.425922/) dit 
is een plugin voor VS 2015, 2017 word op het moment nog niet ondersteund maar daar wordt wel aan gewerkt.  

Unity's shader files zijn zelf te downloaden en te bekijen. Ga hievoor naar de Unity archive site en gebruik de dropdown menu's van de gewenste versie 
om de 'Built in shaders' te downloaden van deze versie.  
*[Unity: archive](https://unity3d.com/get-unity/download/archive)*  

Unity's nieuwe
Unity standard 'mega shader' 
Properties
SubShaders
Passes

vert en frag functions

CGPROGRAM en ENDCG

#### Sub onderdeel

tekst van het sub onderdeel

```
fixed4 fragFunct(v2f IN) : SV_Target
{
	fixed4 col = tex2D(_MainTex, IN.uv);
	return col * _Color;
}
```

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LevelOfDetail.md)