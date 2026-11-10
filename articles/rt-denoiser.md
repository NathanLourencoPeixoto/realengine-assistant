id: rt-denoiser
kind: concept
title: Denoiser de ray tracing (Fotorrealista) | Ray tracing denoiser (Photoreal)
keys: denoiser, denoise, ruido, ruído, noise, granulado, chuviscado, pontilhado, grain, speckle, reblur, relax, nrd, ray reconstruction, gi ray traced, gi por raio, iluminacao indireta por raio, ray traced gi, reflexo aspero, rough reflection, reflexo borrado, glossy reflection, sombra suave ruidosa, noisy soft shadow, fantasma, ghosting, rastro, trail, fotorrealista ruido, photoreal noise, oclusao de contato, contact shadow gi, REALENGINE_DENOISER, REALENGINE_DEN_DEBUG
--- pt
```diagram steps
Passe principal: 1 raio de GI difusa + 1 raio de reflexo (GGX) por pixel
Pré-borrão (8 amostras ao redor)
Histórico: reprojetado, só no mesmo ator, mesma normal, mesma profundidade
Pós-borrão (largo enquanto o histórico é curto) e estabilização
Cor final: difuso x albedo + reflexo x peso + luz x visibilidade da sombra
```
No estilo **Fotorrealista** (e no **Vídeo-realista**) a engine troca a luz indireta do cache de superfície por **raios de verdade**, como um path tracer em tempo real, e passa tudo por **um denoiser só**, no estilo do ReBLUR da NVIDIA:
- **GI difusa:** um raio por pixel até 30 m (o que ele acerta é iluminado pelo cache de superfície). Cantos e objetos encostados ganham a sombra de contato que o cache não tem. Superfícies com lightmap continuam com o lightmap.
- **Reflexos ásperos:** um raio na direção sorteada pelo lóbulo GGX (rugosidade entre a de reflexo nítido e 0,9). Os reflexos espelhados continuam com o raio exato, sem filtro.
- **Sombras de luzes de área e de muitas luzes:** a visibilidade sorteada pelas luzes passa pelo mesmo filtro (no lugar do filtro separado).
- **Sem fantasma:** o histórico só é reaproveitado no **mesmo ator**, com a **mesma normal** e na **mesma profundidade**; o que falha é descartado, nunca misturado. Ele guarda poucos quadros (difuso 64, reflexo 4 a 24 conforme a rugosidade, sombra 8), e um histórico rápido corta o longo quando a luz muda (lâmpada apagada, porta aberta).
- **Custo** (RTX 3060, 1440p Épico): o filtro ~1,6 ms; os raios ~1,5 ms na casa e ~5,6 ms na RPG (folhagem). A casa roda a ~140 fps e a RPG a ~74 fps no Fotorrealista; o Realista não muda (ele nem tem o código dos raios).
- **Só com MSAA desligado** (anti-aliasing temporal/TSR): com MSAA ficam os filtros separados.
- **Erro contra o path tracing de referência** (casa): 11,5% → 7,7%.
- **Depurar:** `REALENGINE_DEN_DEBUG=1` mostra só o difuso, `2` só o reflexo, `3` a visibilidade das sombras, `4` o tamanho do histórico (vermelho curto, verde cheio). `REALENGINE_DENOISER=1` liga em qualquer estilo, `=0` desliga.
--- en
```diagram steps
Main pass: 1 diffuse GI ray + 1 reflection ray (GGX) per pixel
Pre-blur (8 taps around)
History: reprojected, only on the same actor, same normal, same depth
Post-blur (wide while the history is short) and stabilization
Final color: diffuse x albedo + reflection x weight + light x shadow visibility
```
In the **Photoreal** style (and **Video-realistic**) the engine replaces the surface cache's indirect light with **real rays**, like a real-time path tracer, and runs everything through **a single denoiser**, in the style of NVIDIA's ReBLUR:
- **Diffuse GI:** one ray per pixel up to 30 m (what it hits is lit by the surface cache). Corners and objects touching each other get the contact shadow the cache lacks. Lightmapped surfaces keep their lightmap.
- **Rough reflections:** one ray along a direction picked from the GGX lobe (roughness between the sharp-reflection cutoff and 0.9). Mirror-like reflections keep their exact ray, unfiltered.
- **Area-light and many-light shadows:** the stochastic visibility goes through the same filter (instead of the separate one).
- **No ghosting:** the history is reused only on the **same actor**, with the **same normal** and at the **same depth**; anything that fails is dropped, never blended. It keeps few frames (diffuse 64, reflection 4 to 24 by roughness, shadow 8), and a fast history cuts the long one short when the light changes (a lamp turned off, a door opened).
- **Cost** (RTX 3060, 1440p Epic): the filter ~1.6 ms; the rays ~1.5 ms in the house and ~5.6 ms in the RPG (foliage). The house runs at ~140 fps and the RPG at ~74 fps in Photoreal; Realistic is unchanged (it doesn't even have the rays' code).
- **MSAA off only** (temporal AA/TSR): with MSAA the separate filters stay.
- **Error against the path-traced reference** (house): 11.5% → 7.7%.
- **Debug:** `REALENGINE_DEN_DEBUG=1` shows only the diffuse, `2` only the reflection, `3` the shadows' visibility, `4` the history length (red short, green full). `REALENGINE_DENOISER=1` turns it on in any style, `=0` off.
