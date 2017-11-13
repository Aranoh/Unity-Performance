# Lighting Modes Reference Card

[terug naar index](/Index.md#unity-settings)   
[terug naar Light and Shadows](/UnitySettings/LightAndShadows.md)  

| Unity Lighting Modes Reference Card |                     |                       |                       |                     |
|-------------------------------------|---------------------|-----------------------|-----------------------|---------------------|
|                                     |                     |                       |                       |                     |
| Light                               |                     |                       |                       |                     |
|                                     | Receiver            | Receiver              |                       |                     |
| Submode                             | Direct lighting     | Indirect lighting     | Direct lighting       | Indirect lighting   |
| Realtime                            |                     |                       |                       |                     |
|                                     | Dynamic receiver    | Static receiver       |                       |                     |
| Realtime                            | Realtime            | -                     | Realtime              | -                   |
| Realtime GI                         | Realtime            | Realtime Light Probes | Realtime              | Realtime lightmap   |
| Mixed                               |                     |                       |                       |                     |
|                                     | Dynamic receiver    | Static receiver       |                       |                     |
| Baked Indirect                      | Realtime            | Light Probes          | Realtime              | Lightmap            |
| Shadowmask                          | Realtime            | Light Probes          | Realtime              | Lightmap            |
| Distance Shadowmask                 | Realtime            | Light Probes          | Realtime              | Lightmap            |
| Subtractive                         | Realtime            | Light Probes          | Lightmap              | Lightmap            |
| Baked                               |                     |                       |                       |                     |
|                                     | Dynamic receiver    | Static receiver       |                       |                     |
| Baked                               | Light Probes        | Light Probes          | Lightmap              | Lightmap            |
|                                     |                     |                       |                       |                     |
| Shadows                             |                     |                       |                       |                     |
| Submode                             | Receiver            | Receiver              |                       |                     |
| Caster                              | Within shadow dist. | Beyond shadow dist.   | Within shadow dist.   | Beyond shadow dist. |
| Caster                              | Within shadow dist. | Beyond shadow dist.   | Within shadow dist.   | Beyond shadow dist. |
| Realtime                            |                     |                       |                       |                     |
|                                     | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | Shadow map          | -                     | Shadow map            | -                   |
| Static caster                       | Shadow map          | -                     | Shadow map            | -                   |
| Mixed                               |                     |                       |                       |                     |
| Baked Indirect                      | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | Shadow map          | -                     | Shadow map            | -                   |
| Static caster                       | Shadow map          | -                     | Shadow map            | -                   |
|                                     |                     |                       |                       |                     |
| Shadowmask                          | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | Shadow map          | -                     | Shadow map            | -                   |
| Static caster                       | Light Probes        | Light Probes          | Shadowmask            | Shadowmask          |
|                                     |                     |                       |                       |                     |
| Distance Shadowmask                 | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | Shadow map          | -                     | Shadow map            | -                   |
| Static caster                       | Shadow map          | Light Probes          | Shadow map            | Shadowmask          |
|                                     |                     |                       |                       |                     |
| Subtractive                         | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | Shadow map          | -                     | Main light shadow map | -                   |
| Static caster                       | Light Probes        | Light Probes          | Lightmap              | Lightmap            |
| Baked                               |                     |                       |                       |                     |
|                                     | Dynamic receiver    | Static receiver       |                       |                     |
| Dynamic caster                      | -                   | -                     | -                     | -                   |
| Static caster                       | Light Probes        | Light Probes          | Lightmap              | Lightmap            |