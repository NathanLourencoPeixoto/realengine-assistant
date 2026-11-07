id: texture-streaming
kind: concept
title: Streaming de texturas e memória de vídeo | Texture streaming and video memory
keys: streaming, textura borrada, memoria de video, vram, textura baixa resolucao, orcamento de textura, texture pool, blurry texture, out of memory
--- pt
```diagram bars MB
Orçamento (35% da VRAM, ex. 12 GB): 4300
Texturas na tela (resolução cheia): 1800
Fora de vista (no mínimo): 120
```
- Cada material guarda as texturas no tamanho que a tela pede, dentro de um orçamento de 35% da memória de vídeo.
- Perto da câmera sobe para a resolução cheia; longe ou fora de vista desce. Só desce quando a memória aperta (85%).
- No projeto comum nada muda: tudo cabe cheio. Em cenas enormes, uma textura borrada por um instante é ela subindo.
- Para testar com menos memória: `REALENGINE_TEX_BUDGET_MB=1024`. Para desligar: `REALENGINE_TEX_STREAMING=0`.
- Veja também: [Escalabilidade](article:scalability), [Malhas pesadas](article:heavy-meshes).
--- en
```diagram bars MB
Budget (35% of VRAM, e.g. 12 GB): 4300
Textures on screen (full size): 1800
Out of view (at the minimum): 120
```
- Each material keeps its textures at the size the screen asks for, inside a budget of 35% of video memory.
- Near the camera they go up to full size; far or out of view they go down. They only go down when memory is tight (85%).
- In a normal project nothing changes: everything fits at full size. In huge scenes a texture blurry for a moment is it going up.
- To test with less memory: `REALENGINE_TEX_BUDGET_MB=1024`. To turn it off: `REALENGINE_TEX_STREAMING=0`.
- See also: [Scalability](article:scalability), [Heavy meshes](article:heavy-meshes).
