# Lighting Modes Reference Card

[terug naar index](/Index.md#unity-settings)   
[terug naar Light and Shadows](/UnitySettings/LightAndShadows.md)  

<table>
  <tr>
    <th colspan="5" rowspan="2">Unity Lighting Modes Reference Card</th>
  </tr>
  <tr>
  </tr>
  <tr>
    <td colspan="5"><b>Light</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Receiver</td>
    <td colspan="2">Receiver</td>
  </tr>
  <tr>
    <td>Submode</td>
    <td>Direct lighting</td>
    <td>Indirect lighting</td>
    <td>Direct lighting</td>
    <td>Indirect lighting</td>
  </tr>
  <tr>
    <td colspan="5"><b>Realtime</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Realtime</td>
    <td>Realtime</td>
    <td>-</td>
    <td>Realtime</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Realtime GI</td>
    <td>Realtime</td>
    <td>Realtime Light Probes</td>
    <td>Realtime</td>
    <td>Realtime lightmap</td>
  </tr>
  <tr>
    <td colspan="5"><b>Mixed</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Baked Indirect</td>
    <td>Realtime</td>
    <td>Light Probes</td>
    <td>Realtime</td>
    <td>Lightmap</td>
  </tr>
  <tr>
    <td>Shadowmask</td>
    <td>Realtime</td>
    <td>Light Probes</td>
    <td>Realtime</td>
    <td>Lightmap</td>
  </tr>
  <tr>
    <td>Distance Shadowmask</td>
    <td>Realtime</td>
    <td>Light Probes</td>
    <td>Realtime</td>
    <td>Lightmap</td>
  </tr>
  <tr>
    <td>Subtractive</td>
    <td>Realtime</td>
    <td>Light Probes</td>
    <td>Lightmap</td>
    <td>Lightmap</td>
  </tr>
  <tr>
    <td colspan="5"><b>Baked</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td rowspan="2">Baked</td>
    <td rowspan="2">Light Probes</td>
    <td rowspan="2">Light Probes</td>
    <td rowspan="2">Lightmap</td>
    <td rowspan="2">Lightmap</td>
  </tr>
  <tr>
  </tr>
  </table>
  
  <table>
  <tr>
    <td colspan="5"><b>Shadows</b></td>
  </tr>
  <tr>
    <td>Submode</td>
    <td colspan="2">Receiver</td>
    <td colspan="2">Receiver</td>
  </tr>
  <tr>
    <td>Caster</td>
    <td>Within shadow dist.</td>
    <td>Beyond shadow dist.</td>
    <td>Within shadow dist.</td>
    <td>Beyond shadow dist.</td>
  </tr>
  <tr>
    <td>Caster</td>
    <td>Within shadow dist.</td>
    <td>Beyond shadow dist.</td>
    <td>Within shadow dist.</td>
    <td>Beyond shadow dist.</td>
  </tr>
  <tr>
    <td colspan="5"><b>Realtime</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Static caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td colspan="5"><b>Mixed</b></td>
  </tr>
  <tr>
    <td>Baked Indirect</td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td rowspan="2">Static caster</td>
    <td rowspan="2">Shadow map</td>
    <td rowspan="2">-</td>
    <td rowspan="2">Shadow map</td>
    <td rowspan="2">-</td>
  </tr>
  <tr>
  </tr>
  <tr>
    <td>Shadowmask</td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td rowspan="2">Static caster</td>
    <td rowspan="2">Light Probes</td>
    <td rowspan="2">Light Probes</td>
    <td rowspan="2">Shadowmask</td>
    <td rowspan="2">Shadowmask</td>
  </tr>
  <tr>
  </tr>
  <tr>
    <td>Distance Shadowmask</td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td rowspan="2">Static caster</td>
    <td rowspan="2">Shadow map</td>
    <td rowspan="2">Light Probes</td>
    <td rowspan="2">Shadow map</td>
    <td rowspan="2">Shadowmask</td>
  </tr>
  <tr>
  </tr>
  <tr>
    <td>Subtractive</td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>Shadow map</td>
    <td>-</td>
    <td>Main light shadow map</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Static caster</td>
    <td>Light Probes</td>
    <td>Light Probes</td>
    <td>Lightmap</td>
    <td>Lightmap</td>
  </tr>
  <tr>
    <td colspan="5"><b>Baked</b></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2">Dynamic receiver</td>
    <td colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td>Dynamic caster</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td>Static caster</td>
    <td>Light Probes</td>
    <td>Light Probes</td>
    <td>Lightmap</td>
    <td>Lightmap</td>
  </tr>
</table>



<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-s6z2{text-align:center}
.tg .tg-5qg7{font-size:24px;text-align:center}
.tg .tg-wm6t{font-weight:bold;font-size:16px}
.tg .tg-hgcj{font-weight:bold;text-align:center}
.tg .tg-huh2{font-size:14px;text-align:center}
</style>
<table class="tg">
  <tr>
    <th class="tg-5qg7" colspan="5">Unity Lighting Modes Reference Card</th>
  </tr>
  <tr>
    <td class="tg-031e"></td>
    <td class="tg-031e"></td>
    <td class="tg-031e"></td>
    <td class="tg-031e"></td>
    <td class="tg-031e"></td>
  </tr>
  <tr>
    <td class="tg-031e" colspan="5">Light</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Receiver</td>
    <td class="tg-s6z2" colspan="2">Receiver</td>
  </tr>
  <tr>
    <td class="tg-031e">Submode</td>
    <td class="tg-s6z2">Direct lighting</td>
    <td class="tg-s6z2">Indirect lighting</td>
    <td class="tg-s6z2">Direct lighting</td>
    <td class="tg-s6z2">Indirect lighting</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Realtime</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Realtime GI</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Realtime Light Probes</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Realtime lightmap</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Mixed</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Baked Indirect</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Shadowmask</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Distance Shadowmask</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Subtractive</td>
    <td class="tg-s6z2">Realtime</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Lightmap</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Baked</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Baked</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Lightmap</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Shadows</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Submode</td>
    <td class="tg-s6z2" colspan="2">Receiver</td>
    <td class="tg-s6z2" colspan="2">Receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Caster</td>
    <td class="tg-s6z2">Within shadow dist.</td>
    <td class="tg-s6z2">Beyond shadow dist.</td>
    <td class="tg-s6z2">Within shadow dist.</td>
    <td class="tg-s6z2">Beyond shadow dist.</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Caster</td>
    <td class="tg-s6z2">Within shadow dist.</td>
    <td class="tg-s6z2">Beyond shadow dist.</td>
    <td class="tg-s6z2">Within shadow dist.</td>
    <td class="tg-s6z2">Beyond shadow dist.</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Realtime</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Static caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Mixed</td>
  </tr>
  <tr>
    <td class="tg-hgcj">Baked Indirect</td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Static caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
  </tr>
  <tr>
    <td class="tg-hgcj">Shadowmask</td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Static caster</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Shadowmask</td>
    <td class="tg-s6z2">Shadowmask</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
  </tr>
  <tr>
    <td class="tg-hgcj">Distance Shadowmask</td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Static caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">Shadowmask</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2"></td>
  </tr>
  <tr>
    <td class="tg-hgcj">Subtractive</td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">Shadow map</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">Main light shadow map</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-huh2">Static caster</td>
    <td class="tg-huh2">Light Probes</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Lightmap</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
  <tr>
    <td class="tg-wm6t" colspan="5">Baked</td>
  </tr>
  <tr>
    <td class="tg-s6z2"></td>
    <td class="tg-s6z2" colspan="2">Dynamic receiver</td>
    <td class="tg-s6z2" colspan="2">Static receiver</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Dynamic caster</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">-</td>
    <td class="tg-s6z2">-</td>
  </tr>
  <tr>
    <td class="tg-s6z2">Static caster</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Light Probes</td>
    <td class="tg-s6z2">Lightmap</td>
    <td class="tg-s6z2">Lightmap</td>
  </tr>
</table>



| Unity Lighting Modes Reference Card |                     |                       |                       |                     |
|-------------------------------------|---------------------|-----------------------|-----------------------|---------------------|
|                                     |                     |                       |                       |                     |
| **Light**                           |                     |                       |                       |                     |
|                                     | **Receiver**        |                       | **Receiver**          |                     |
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