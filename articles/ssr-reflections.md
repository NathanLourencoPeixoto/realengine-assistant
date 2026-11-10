id: ssr-reflections
kind: concept
title: Reflexos em tela (SSR) | Screen space reflections (SSR)
keys: ssr, screen space reflections, reflexos em tela, reflexo no chao, floor reflection, chao molhado, wet floor, espelho, mirror, chao polido, polished floor, reflexo sem ray tracing, reflections without ray tracing, reflexo no medio, reflection medium preset, reflexo some na borda, reflection disappears at the edge
--- pt
```diagram steps
Superfície lisa (rugosidade abaixo de 0,35): segue o raio refletido na tela
Pela profundidade e pela cor do quadro anterior: onde o raio passa atrás de algo, é o que ela reflete
Achou: o reflexo do céu e das sondas vira o da tela; não achou (fora da tela): fica o de antes
```
Os **reflexos em tela** mostram, em chão molhado, piso polido, metal e água, os objetos que estão na tela. Eles entram onde **nenhum raio traça reflexos**: nos presets **Baixo** e **Médio** e nas placas sem ray tracing. Do Alto para cima, numa placa com ray tracing, o reflexo é por raio, mais exato e com o que está fora da tela.
- **O que aparece:** só o que a câmera vê. Um objeto fora da tela, ou atrás de outro, não reflete. Perto das bordas da tela, o reflexo some aos poucos para o do céu e das sondas.
- **Onde:** superfícies com **Roughness** abaixo de 0,35; entre 0,2 e 0,35 ele vai se misturando com o reflexo borrado.
- **Custo:** cerca de 0,3 a 0,4 ms com um chão espelhado ocupando a maior parte da tela no Médio a 1440p, contando a cópia da cor e da profundidade.
- **Desligar** (teste ou comparação): `REALENGINE_NO_SSR=1`.
--- en
```diagram steps
Smooth surface (roughness below 0.35): follow the reflected ray on screen
Through last frame's depth and color: where the ray passes behind something, that is what it reflects
Found: the sky's and probes' reflection becomes the screen's; not found (off screen): it stays as before
```
**Screen space reflections** show, on wet floors, polished floors, metal and water, the objects that are on screen. They apply where **no ray traces reflections**: in the **Low** and **Medium** presets and on graphics cards without ray tracing. From High up, on a card with ray tracing, the reflection is traced by rays, more exact and including what is off screen.
- **What shows up:** only what the camera sees. An object off screen, or behind another, doesn't reflect. Near the screen's edges, the reflection fades into the sky's and probes'.
- **Where:** surfaces with **Roughness** below 0.35; between 0.2 and 0.35 it blends into the blurred reflection.
- **Cost:** about 0.3 to 0.4 ms with a mirror floor filling most of the screen on Medium at 1440p, counting the copy of the color and depth.
- **Turn off** (a test or a comparison): `REALENGINE_NO_SSR=1`.
