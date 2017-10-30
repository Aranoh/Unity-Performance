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

Unity maakt gebruik van een globale shader. In deze shader worden heel veel verschillende effecten gebruikt. Deze Unity shader heeft zelf geen code 
in zijn shader file staan maar alleen verwijzingen naar andere shaders. Het nadeel van deze grote Unity shader is dat er ook altijd wat berekend 
zal worden waar je geen gebruik van maakt. Hierom is het belangrijk om de mobiele shaders te gebruiken. Deze shaders maken niet gebruik van een 
globale overkoepelende shader en is vaak zuiniger in gebruik.

#### Properties

Dit stuk is bedoeld voor Unity zelf. in het properties gedeelte kan je verschillende dingen in de inspector terug laten komen. Denk hierbij aan dingen 
zoals een texture, een color filter, een Normal map of Parallax map. 

Variabelen die gebruikt worden in een .shader file zijn:
* 2D 	- gebruikt voor een afbeelding of texture.
* Range	- Net als in Unity een getal tussen twee getallen selecteren.
* Float	- Zoals C#'s float, een simpel getal.
* Color	- Kleur selecteren, 4 waardes tussen 0 en 1 voor RGBA.  



```
Properties
{
	_MainTex("Albedo", 2D) = "white" {}
	_Color("Color", Color) = (1,1,1,1)
	
	
	

#### SubShaders
 

* Unity standard 'mega shader'   
* Properties  
* SubShaders  
* Passes  

* vert en frag functions  

* CGPROGRAM en ENDCG  

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