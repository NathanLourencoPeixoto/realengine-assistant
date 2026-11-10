id: far-probes
kind: concept
title: Luz indireta ao longe (sondas distantes) | Distant indirect light (far probes)
keys: luz indireta longe, gi longe, gi distante, far field, far probes, sondas distantes, cascata de sondas, probe cascade, montanha escura, predio longe sem luz, distant building lighting, paisagem grande gi, landscape gi, horizonte iluminacao, REALENGINE_NO_FAR_PROBES
--- pt
```diagram steps
Perto da câmera: sondas a cada 2 m (cerca de 64 m em volta)
Além delas: uma segunda grade, sondas a cada 16 m (cerca de 512 m)
Na borda as duas se misturam, sem emenda
Liga sozinha quando a cena é maior que a grade perto
```
A iluminação global usa **sondas** (pontos que medem a luz em todas as direções). Antes, além de ~64 m da câmera só havia a luz do céu: um prédio ou uma colina distante não recebia o rebate do chão nem ficava mais escura onde algo a encobria. Agora uma **segunda grade de sondas**, 8 vezes mais espaçada, cobre até ~512 m.
- **Automático:** liga quando a cena passa da grade perto (vilas, paisagens). Uma casa ou uma sala não paga nada.
- **Custo** (RTX 3060, Épico): de quase zero numa vila a ~0,45 ms numa paisagem grande.
- **Sem emenda:** nas últimas sondas da grade perto as duas se misturam.
- Para comparar sem ela: `REALENGINE_NO_FAR_PROBES=1`.
--- en
```diagram steps
Near the camera: probes every 2 m (about 64 m around)
Past them: a second grid, probes every 16 m (about 512 m)
At the edge the two blend, no seam
Turns on by itself when the scene is bigger than the near grid
```
Global illumination uses **probes** (points that measure light in every direction). Before, past ~64 m from the camera there was only the sky's light: a distant building or hill got no bounce from the ground and no darkening where something covered it. Now a **second grid of probes**, 8 times wider apart, reaches ~512 m.
- **Automatic:** it turns on when the scene goes past the near grid (villages, landscapes). A house or a room pays nothing.
- **Cost** (RTX 3060, Epic): from almost nothing in a village to ~0.45 ms in a large landscape.
- **No seam:** across the near grid's last probes the two blend.
- To compare without it: `REALENGINE_NO_FAR_PROBES=1`.
