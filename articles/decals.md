id: decals
kind: concept
title: Decals: sujeira, sangue, marcas | Decals: dirt, blood, marks
keys: decal, decals, decal actor, ator decal, colocar sangue, sangue na parede, mancha na parede, sujeira no chao, sujeira, dirt, grime, sangue, blood, marca de bala, bullet hole, rachadura, crack, mancha, stain, pichacao, graffiti, projetar material, project material, spawn decal at location, decal material, material do decal, fade by angle, life span, tempo de vida, sort order
--- pt
```diagram steps
Adicionar > Efeitos Visuais > Decal
A seta (o X do ator) aponta para a superfície
Details > Decal: o Material do Decal, a Opacidade, o Fade pelo Ângulo
Escala: o tamanho da caixa (1 = 2 m de lado)
```
Um **Decal** projeta um material sobre o que está dentro da caixa dele: sujeira no chão, sangue na parede, marcas de bala, rachaduras. O decal recebe luz e sombra como a superfície embaixo.
- O material pode ser qualquer um: a **cor** e o **Alpha** do Principled (a parte que aparece), a **normal**, a **rugosidade** e o **metálico** vão por cima da superfície. O exemplo **M_DecalGrime** usa um degradê redondo com ruído no Alpha.
- **Fade pelo Ângulo**: superfícies muito viradas em relação ao decal somem aos poucos, sem borrar as laterais. **Distância do Fade**: some longe da câmera. **Ordem**: quem fica por cima quando dois se sobrepõem.
- **Tempo de Vida** e **Desaparecer**: o decal some aos poucos e o ator vai embora. Serve para marcas de bala e sangue.
- **Blueprint**: o nó **Spawn Decal at Location** (Location, Rotation apontando para a superfície, Decal Size, Life Span; o material no Details) devolve o ator. Num Line Trace, use o Impact Point e gire o decal contra a Impact Normal.
- **Não aparece?** Confira se a seta aponta para a superfície e se a caixa (a escala) a alcança. Malhas Masked ou translúcidas não recebem decal.
--- en
```diagram steps
Add > Visual Effects > Decal
The arrow (the actor's X) points at the surface
Details > Decal: the Decal Material, Opacity, Fade by Angle
Scale: the box's size (1 = 2 m across)
```
A **Decal** projects a material onto what is inside its box: dirt on the floor, blood on a wall, bullet holes, cracks. It is lit and shadowed like the surface under it.
- Any material works: the Principled's **color** and **Alpha** (the share that shows), the **normal**, **roughness** and **metallic** go over the surface. The **M_DecalGrime** example has a round falloff with noise in its Alpha.
- **Fade by Angle**: surfaces turned far from facing it fade out (no smear down the sides). **Fade Distance**: it fades far from the camera. **Sort Order**: which one is on top when two overlap.
- **Life Span** and **Fade Out**: it fades and its actor goes. Bullet holes, blood.
- **Blueprint**: the **Spawn Decal at Location** node (Location, Rotation pointing at the surface, Decal Size, Life Span; the material in Details) returns the actor. From a Line Trace, use the Impact Point and turn the decal against the Impact Normal.
- **Not showing?** Check that the arrow points at the surface and that the box (the scale) reaches it. Masked or translucent meshes don't take decals.
