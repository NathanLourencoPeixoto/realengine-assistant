id: shadows-pro
kind: concept
title: Sombras: virtuais, por raio, PCSS | Shadows: virtual, ray traced, PCSS
keys: sombra aparece do nada, shadow pops in, sombra surge de perto, transicao de sombra, shadow transition, fade de sombra, shadow fade, sombra, sombras, shadow, virtual shadow maps, vsm, pcss, sombra suave, sombra serrilhada, sombra pixelada, sombra de longe, ray traced shadows
--- pt
- **Sol:** sombras virtuais em clipmap com cache (só redesenha o que mudou), suavidade física (PCSS) e raio para o que está perto do bloqueador.
- **Luzes locais:** por raio quando há ray tracing; luzes de área com penumbra filtrada.
- **Masked** (folhas, grades): a sombra respeita o recorte do material.
- Sombra pixelada ou sumindo de longe: suba a escalabilidade de sombras ou aproxime a câmera; luz Static com lightmap custa menos.
- **Transições suaves:** ao chegar perto ou se afastar, a sombra passa de um nível de detalhe para o outro aos poucos (fade nos últimos 30% de cada nível) e a troca mapa → raio é uma rampa; no fim do alcance a sombra some aos poucos. Nada aparece "do nada" no personagem.
--- en
- **Sun:** cached clipmap virtual shadows (only what changed is redrawn), physical softness (PCSS) and rays near the blocker.
- **Local lights:** ray traced when there's ray tracing; area lights with filtered penumbra.
- **Masked** (leaves, grates): the shadow follows the material's cutout.
- Pixelated shadow or fading far away: raise the shadows' scalability or bring the camera closer; a Static light with a lightmap costs less.
- **Smooth transitions:** walking up or away, a shadow goes from one level of detail to the next gradually (a fade over each level's last 30%) and the map-to-ray switch is a ramp; at the end of the range the shadow fades out. Nothing pops in on a character.
