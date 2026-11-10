id: hair-groom
kind: concept
title: Cabelo em fios (Groom) | Hair in strands (Groom)
keys: cabelo de verdade em fios, cabelo em fios no personagem, cabelo, hair, fios, strands, groom, groom component, componente groom, cabelo realista, realistic hair, pelo, fur, barba, beard, marschner, melanina, melanin, ruivo, red hair, loiro, blond, cacheado, curly, ondulado, wavy, cabelo comprido, long hair, hair cards, cards de cabelo, sombra do cabelo, hair shadow, REALENGINE_NO_HAIR
--- pt
```diagram steps
Adicione o componente Groom ao ator da cabeça
Os fios nascem no topo da malha, penteados para trás
Gravidade, cachos e mechas dão a forma
Cada fio é iluminado como fibra (brilho duplo, luz atravessando)
```
O **Groom** (como o Groom Component da Unreal) faz crescer cabelo em **fios de verdade** sobre a malha do ator, em vez de cartões com textura.
- **Como usar:** selecione o ator da cabeça, **+ Adicionar > Groom**. Escolha um **Preset** (Curto, Comprido, Ondulado, Cacheado) e ajuste: **Strands** (quantos fios), **Length**, **Curl** e **Curl Frequency** (cachos), **Gravity** (quanto cai), **Clumping** (mechas), **Scalp** (até onde desce na cabeça) e **Hairline** (a testa: o ator olha para +X).
- **Cor:** **Melanin** (0 loiro claro ... 1 preto) e **Redness** (ruivo), como na Unreal; **Dye** tinge por cima; **Roughness** alarga o brilho.
- **Luz:** os três brilhos de um fio (o branco, o colorido mais abaixo e a luz atravessando contra o sol) e a sombra que o cabelo faz em si mesmo (uma grade de densidade).
- **Longe:** com **LOD** ligado, menos fios e mais largos: a mesma aparência por menos trabalho.
- **Custo** (RTX 3060, Épico): ~0,3-0,7 ms com 20 mil fios numa cabeça perto da câmera.
- **Ainda não:** o cabelo não faz sombra na pele nem se mexe com física; os fios nascem da forma da malha (elipsoide), não de uma pintura.
- Para comparar sem: `REALENGINE_NO_HAIR=1`. Cena de teste: `hair`.
--- en
```diagram steps
Add the Groom component to the head's actor
The strands grow over the top of the mesh, combed back
Gravity, curls and clumps give the shape
Each strand is lit as a fiber (two highlights, light coming through)
```
The **Groom** (like Unreal's Groom Component) grows hair in **real strands** over the actor's mesh, instead of textured cards.
- **How to use:** select the head's actor, **+ Add > Groom**. Pick a **Preset** (Short, Long, Wavy, Curly) and adjust: **Strands** (how many), **Length**, **Curl** and **Curl Frequency**, **Gravity** (how much it falls), **Clumping** (locks), **Scalp** (how far down the head it grows) and **Hairline** (the forehead: the actor looks along +X).
- **Color:** **Melanin** (0 light blond ... 1 black) and **Redness** (red hair), as in Unreal; **Dye** tints over it; **Roughness** widens the shine.
- **Light:** a fiber's three highlights (the white one, the colored one below it and the light coming through against the sun) and the shadow the hair casts on itself (a density grid).
- **Far away:** with **LOD** on, fewer strands, wider: the same look for less work.
- **Cost** (RTX 3060, Epic): ~0.3-0.7 ms with 20 thousand strands on a head near the camera.
- **Not yet:** the hair casts no shadow on the skin and doesn't move with physics; the strands grow from the mesh's shape (an ellipsoid), not from a painting.
- To compare without it: `REALENGINE_NO_HAIR=1`. Test scene: `hair`.
