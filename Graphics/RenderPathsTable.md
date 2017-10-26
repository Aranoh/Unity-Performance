# Render paths table  

[terug naar index](/Index.md#scripting)   
[terug naar Pooling](/Graphics/ShadersPostProcessing.md) 

||Deferred|Forward|Legacy Deferred|Vertex Lit|
|:--:|:--:|:--:|:--:|:--:|
|Features|  

|Per-pixel lighting (normal maps, light cookies)|Yes|Yes|Yes|-|
|Realtime shadows|Yes|With caveats|Yes|-|
|Reflection Probes|Yes|Yes|-|-|
|Depth&Normals Buffers|Yes|Additional render passes|Yes|-|
|Soft Particles|Yes|-|Yes|-|
|Semitransparent objects|-|Yes|-|Yes|
|Anti-Aliasing|-|Yes|-|Yes|
|Light Culling Masks|Limited|Yes|Limited|Yes|
|Lighting Fidelity|All per-pixel|Some per-pixel|All per-pixel|All per-vertex|
|Performance|  

|Cost of a per-pixel Light|Number of pixels it illuminates|Number of pixels * Number of objects it illuminates|Number of pixels it illuminates|-|
|Number of times objects are normally rendered|1|Number of per-pixel lights|2|1|
|Overhead for simple scenes|High|None|Medium|None|
|Platform Support|  

|PC (Windows/Mac)|Shader Model 3.0+ & MRT|All|Shader Model 3.0+|All|
|Mobile (iOS/Android)|OpenGL ES 3.0 & MRT, Metal (on devices with A8 or later SoC)|All|OpenGL ES 2.0|All|
|Consoles|XB1, PS4|All|XB1, PS4, 360|-|