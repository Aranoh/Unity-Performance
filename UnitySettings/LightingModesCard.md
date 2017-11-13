# Lighting Modes Reference Card

[terug naar index](/Index.md#unity-settings)   
[terug naar Light and Shadows](/UnitySettings/LightAndShadows.md)  

### Lights
<table>
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
  <td colspan="5"> </td>
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
  
  ### Shadows 
  <table>
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
  <td colspan="5"> </td>
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

[Unity Docs: Baked Indirect](https://docs.unity3d.com/Manual/LightMode-Mixed-BakedIndirect.html)  
[Unity Docs: Shadowmask](https://docs.unity3d.com/Manual/LightMode-Mixed-ShadowmaskMode.html)  
[Unity Docs: Subtractive](https://docs.unity3d.com/Manual/LightMode-Mixed-Subtractive.html)  
