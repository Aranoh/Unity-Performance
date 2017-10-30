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

Variabelen die veel gebruikt worden in een .shader file zijn:
* 2D 	- Gebruikt voor een afbeelding of texture.
* Range	- Net als in Unity een getal tussen twee getallen selecteren.
* Float	- Zoals C#'s float, een simpel getal.
* Color	- Kleur selecteren, 4 waardes tussen 0 en 1 voor RGBA.  

```
Properties
{
	_MainTex("Albedo", 2D) = "white" {}
	_Color("Color", Color) = (1,1,1,1)
}
```	 

#### SubShaders
 
Binnen een shader kunnen een paar verschillende SubShaders gemaakt worden. Een SubShader kan gebruikt worden om binnen een shader onderscheid te 
maken in in wanneer iets wel of niet gedaan moet worden. Wanneer een shader gebruikt word zal altijd de eerste mogelijke subshader gebruikt worden. 
Met tags en LOD waardes kan aangegeven worden wanneer de SubShader gebruikt moet worden.

```
SubShader
{
Tags { "RenderType"="Opaque" "PerformanceChecks"="False" }
LOD 150

// Rest of SubShader code
}
```

#### Passes

Binnen een SubShader kunnen verschillende passes gebruikt worden. Elke pass heeft zijn eigen functionaliteit en voegt vaak een van de verschillende 
filters toe. Zo kun je bijvoorbeeld een pass maken voor het toepassen van de maintexture, een tweede pass voor de kleur filter en een 3e pass voor 
het berekenen van reflectie of normal mapping. Binnen een pass kunnen ook weer tags gebruikt worden om bepaalde passes niet te doen.  

```
Pass
{
	Name "FORWARD"
	Tags { "LightMode" = "ForwardBase" }
}
```  
#### CGProgram en ENDCG  

Niet alle code binnen een .shader file worden gedraait op je video kaart. Een deel van de shader is voor de Unity engine zelf en is er zodat 
Unity weet welke shaders hij moet gebruiken, textures en fields kan invullen en de goede SubShaders en passes draaien. Om aan te geven welke 
code bestemd is voor de grafische kaart maken we binnen een .shader file gebruik van de annotaties 'CGPROGRAM' en 'ENDCG' alle code binnen deze 
blokken is bedoeld voor de grafische kaart. 

```
SubShader
{
	Pass
	{
		Name "First Pass"
		CGPROGRAM
		// Shader code running on the video card
		ENDCG
	}
	Pass
	{
		Name "Second Pass"
		CGPROGRAM
		// More shader code running on the video card
		ENDCG
	}
}
```

#### Vert en Frag functies

Binnen de .shader files word gebruik gemaakt van twee verschillende functies.  

Een vert functie die kijkt naar alle verschillende vertices en deze eventueel aanpast met een van de verschillende filters. Een vert functie 
kan gebruikt worden bij bijvoorbeeld een outline om je model heen, door het naar buiten verplaatsen van de vertices en het twee keer tekenen 
van deze verices kan bijvoorbeeld een outline of glow gemaakt worden.

Frag functies bekijken elke pixel van het model, deze functie kan gebruikt worden om b.v. de kleuren van de texture op de goede plek te 
renderen of om een kleur filter over dit texture te berekenen.

Door het combineren van outputs van deze twee functies kunnen geavanceerde en hele mooie dingen gemaakt worden. (b.v. reflection, bumpmapping en shadows)

#### Basic Shader example

Om een beter beeld te krijgen van hoe de basic shader functionaliteit eruit ziet heb ik hieronder een .shader file gemaakt met alleen alle essentiele 
functies die een shader hoort te bevatten. De enige twee dingen die deze shader doet is de vertices op de goede plek zetten en een texture gebruiken 
om alle kleuren op de goede plek te renderen. 

```
Shader "Performing/Base" //Name and location of the shader in Unity Editor
{
	// Setting properties visible in Unity Editor
	Properties
	{
		_MainTex("Texture", 2D) = "white" {}
		_Color("Mix Color", Color) = (1, 1, 1, 1)
		_ExtrudeAmount("Extrude Amount", Range(0 , .1)) = .1
	}
		// First and only SubShader in this .shader file
		SubShader
		{
			// First and only Pass in this SubShader
			Pass
			{
			// Start of code running on graphics card
			CGPROGRAM
			// Letting the program know what functions we are using
			#pragma vertex vertFunct
			#pragma fragment fragFunct

			#include "UnityCG.cginc"

			// Struct to pass to vert function having all info needed in this function
			struct appdata
			{
				float4 vertex : POSITION;
				float2 uv : TEXCOORD0;
				float3 normal : NORMAL;
			};

			// Struct to pass to frag function having all info needed in this function
			struct v2f
			{
				float2 uv : TEXCOORD0;
				float4 position : SV_POSITION;
			};
			
			// Loading above properties in the CG code
			sampler2D _MainTex;
			float4 _Color;
			float _ExtrudeAmount;

			// Vert function using the appdata struct fields to correctly set its vertices
			v2f vertFunct(appdata IN)
			{
				v2f OUT;
				OUT.position = UnityObjectToClipPos(IN.vertex);
				OUT.uv = IN.uv;
				return OUT;
			}

			// Frag function using the v2f struct fields to set the color of each pixel
			fixed4 fragFunct(v2f IN) : SV_Target
			{
				fixed4 col = tex2D(_MainTex, IN.uv);
				return col * _Color;
			}
			// End of code running on graphics card
			ENDCG
		}
	}
}
```

---
[![Last Page](/Afbeeldingen/Arrow_back_small.png)](/Scripting/GarbageCollector.md) [![Next Page](/Afbeeldingen/Arrow_next_small.png)](/Graphics/LevelOfDetail.md)