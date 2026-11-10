id: fire
kind: concept
title: Fogo de verdade (simulado) | Real fire (simulated)
keys: fogo, fire, fazer fogueira, fogueira com fumaca, fogueira com fumaça, simulated fire, fire like niagara, niagara fluids fire, fire fluid simulation, chama, flame, fogueira, campfire, tocha, torch, vela, candle, fumaça, fumaca, smoke, incendio, queimar, burn, niagara fluids, fluido, gas, simulação de fogo, fire simulation, labareda, brasa, luz do fogo tremendo, flicker, REALENGINE_NO_FIRE
--- pt
```diagram steps
Adicione o ator Fire (Adicionar > Efeitos Visuais)
O combustível na base queima e vira calor e fumaça
O calor sobe e gira (uma simulação de gás na GPU)
A chama brilha pela temperatura; a luz do ator treme junto
```
O **Fire** é fogo **simulado de verdade**, como o Niagara Fluids da Unreal: um gás numa grade 3D na GPU, não uma animação pronta.
- **Como usar:** **Adicionar > Efeitos Visuais > Fire**. Ele já vem com uma **luz** que treme com a chama e faz sombra. Escolha um **Preset** (Fogueira, Tocha, Fogueira Grande, Vela) e ajuste.
- **Forma:** **Width** e **Height** (a caixa do fogo; o ator fica dentro da chama), **Emitter Radius** (a base que queima), **Fuel** (0 apaga), **Burn Rate**, **Heat**, **Buoyancy** (quanto sobe), **Vorticity** e **Turbulence** (as línguas e os redemoinhos).
- **Aparência:** **Brightness** (a chama em nits), **Smoke**, **Smoke Fade**, **Smoke Density** e **Smoke Albedo** (fuligem escura ... vapor claro). A chama tem a cor do calor (vermelho escuro, laranja, amarelo); a fumaça escurece o que está atrás e recebe a sombra de si mesma ao sol.
- **Qualidade:** **Resolution** (células na largura) e **Pressure Iterations**: mais fino, mais caro.
- **Custo** (RTX 3060, Épico): ~0,8 ms numa fogueira de 40 células de largura.
- **Ainda não:** o fogo não se espalha sozinho pelos objetos nem reage ao vento do clima ou ao jogador.
- Para comparar sem: `REALENGINE_NO_FIRE=1`. Cena de teste: `fire`.
--- en
```diagram steps
Add the Fire actor (Add > Visual Effects)
The fuel at its base burns into heat and smoke
The heat rises and swirls (a gas simulation on the GPU)
The flame glows by its temperature; the actor's light flickers with it
```
**Fire** is **truly simulated** fire, like Unreal's Niagara Fluids: a gas on a 3D grid on the GPU, not a canned animation.
- **How to use:** **Add > Visual Effects > Fire**. It comes with a **light** that flickers with the flame and casts shadows. Pick a **Preset** (Campfire, Torch, Bonfire, Candle) and adjust.
- **Shape:** **Width** and **Height** (the fire's box; the actor sits inside the flame), **Emitter Radius** (the burning base), **Fuel** (0 puts it out), **Burn Rate**, **Heat**, **Buoyancy** (how much it rises), **Vorticity** and **Turbulence** (the tongues and the swirls).
- **Look:** **Brightness** (the flame in nits), **Smoke**, **Smoke Fade**, **Smoke Density** and **Smoke Albedo** (dark soot ... light steam). The flame has the color of its heat (dark red, orange, yellow); the smoke darkens what is behind it and takes its own shadow in the sun.
- **Quality:** **Resolution** (cells across) and **Pressure Iterations**: finer costs more.
- **Cost** (RTX 3060, Epic): ~0.8 ms for a campfire 40 cells across.
- **Not yet:** the fire doesn't spread over objects by itself nor react to the weather's wind or the player.
- To compare without it: `REALENGINE_NO_FIRE=1`. Test scene: `fire`.
