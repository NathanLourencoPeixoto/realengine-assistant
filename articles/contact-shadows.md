id: contact-shadows
kind: concept
title: Sombras de contato | Contact shadows
keys: sombra de contato, sombras de contato, contact shadow, contact shadows, sombra no pe do objeto, objeto flutuando, object floating, peter panning, sombra descolada, detached shadow, sombra fina, fine shadow detail, sombra pequena some, small shadow missing, sombra em tela, screen space shadow
--- pt
```diagram steps
O mapa de sombra do sol: bom de longe, mas os detalhes pequenos somem (o objeto parece flutuar)
Em cada pixel com sol: alguns passos na tela em direção ao sol, comparando com a profundidade
Algo no caminho: a parte do sol daquele pixel escurece (só ela; o céu e o resto da luz ficam)
```
As **sombras de contato** completam a sombra do sol nos detalhes pequenos: o pé de uma cadeira, uma pedra no chão, os vãos de uma grade. Sem elas, o objeto pode parecer flutuar, porque o mapa de sombra não tem resolução para o último centímetro.
- **Quando ligam sozinhas:** sempre que o sol é sombreado só pelo mapa. Isso acontece no preset **Baixo** e nas placas de vídeo sem ray tracing. Do Médio para cima, numa placa com ray tracing, um raio já acha os bloqueadores perto do sol (o híbrido), e o resultado é exato.
- **Como funcionam:** depois do passe principal, no mesmo passe do AO em tela, cada pixel iluminado pelo sol anda 12 passos em direção a ele, por uma distância que cresce com a distância da câmera (8 cm perto, até 1,5 m longe). Se algo na tela estiver na frente, só a parte do sol daquele pixel escurece.
- **Custo:** dentro do ruído da medida no Baixo, porque o AO em tela já lê a profundidade.
- **Desligar** (teste ou comparação): `REALENGINE_NO_CONTACT=1`.
--- en
```diagram steps
The sun's shadow map: good from afar, but small details vanish (the object seems to float)
At each sunlit pixel: a few steps on screen toward the sun, compared with the depth
Something in the way: that pixel's share of sunlight darkens (only it; the sky and the rest of the light stay)
```
**Contact shadows** complete the sun's shadow in the small details: a chair's foot, a stone on the ground, the gaps in a fence. Without them an object can seem to float, because the shadow map has no resolution for the last centimeter.
- **When they turn on by themselves:** whenever the sun is shaded by its map alone. That happens in the **Low** preset and on graphics cards without ray tracing. From Medium up, on a card with ray tracing, a ray already finds the sun's near blockers (the hybrid), and the result is exact.
- **How they work:** after the main pass, in the same pass as the screen space AO, each sunlit pixel takes 12 steps toward the sun, over a distance that grows with the distance from the camera (8 cm near, up to 1.5 m far). If something on screen is in front, only that pixel's share of sunlight darkens.
- **Cost:** within the measurement's noise on Low, because the screen space AO already reads the depth.
- **Turn off** (a test or a comparison): `REALENGINE_NO_CONTACT=1`.
