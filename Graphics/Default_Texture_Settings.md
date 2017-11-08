# Post processing effects table

[terug naar index](/Index.md#graphics)   
[terug naar Textures](/Graphics/Textures.md) 

|                             Platform | Color model |        None |       Normal quality (Default) |                   High quality | Low quality (higher performance) |
|-------------------------------------:|------------:|------------:|-------------------------------:|-------------------------------:|---------------------------------:|
| Windows, Linux, macOS, PS4, XBox One |         RGB |  RGB 24 bit |            RGB Compressed DXT1 |          RGB(A) Compressed BC7 |              RGB Compressed DXT1 |
|                                      |        RGBA | RGBA 32 bit |           RGBA Compressed DXT5 |          RGB(A) Compressed BC7 |             RGBA Compressed DXT5 |
|                                      |         HDR |   RGBA Half |            RGB Compressed BC6H |            RGB Compressed BC6H |              RGB Compressed BC6H |
|                                WebGL |         RGB |  RGB 24 bit |            RGB Compressed DXT1 |            RGB Compressed DXT1 |              RGB Compressed DXT1 |
|                                      |        RGBA | RGBA 32 bit |           RGBA Compressed DXT5 |           RGBA Compressed DXT5 |             RGBA Compressed DXT5 |
|          Android (default subTarget) |         RGB |  RGB 24 bit |            RGB Compressed ETC2 |            RGB Compressed ETC2 |              RGB Compressed ETC2 |
|                                      |        RGBA | RGBA 32 bit |           RGBA Compressed ETC2 |           RGBA Compressed ETC2 |             RGBA Compressed ETC2 |
| iOS                                  | RGB         | RGB 24 bit  | RGB Compressed PVRTC 4 bits    | RGB Compressed PVRTC 4 bits    | RGB Compressed PVRTC 2 bits      |
|                                      | RGBA        | RGBA 32 bit | RGBA Compressed PVRTC 4 bits   | RGBA Compressed PVRTC 4 bits   | RGBA Compressed PVRTC 2 bits     |
| tvOS                                 | RGB         | RGB 24 bit  | RGB Compressed ASTC 6x6 block  | RGB Compressed ASTC 4x4 block  | RGB Compressed ASTC 8x8 block    |
|                                      | RGBA        | RGBA 32 bit | RGBA Compressed ASTC 6x6 block | RGBA Compressed ASTC 4x4 block | RGBA Compressed ASTC 8x8 block   |
| Tizen, Samsung TV                    | RGB         | RGB 24 bit  | RGB Compressed ETC             | RGB Compressed ETC             | RGB Compressed ETC               |
|                                      | RGBA        | RGBA 32 bit | RGBA 16 bit                    | RGBA 16 bit                    | RGBA 16 bit                      |