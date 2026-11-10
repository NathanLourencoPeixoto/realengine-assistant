id: parallax
kind: concept
title: Parallax: relevo sem polígonos | Parallax: depth without polygons
keys: parallax, parallax occlusion, pom, relevo no material, relevo sem poligonos, pedras no material, relevo, profundidade, depth, displacement, deslocamento, height map, mapa de altura, altura, height, calcamento, cobblestones, tijolos, bricks, pedras, stones, rejunte, mortar, superficie afundada, sunken surface, microdeslocamento, micro displacement
--- pt
```diagram steps
Material Opaque: um nó Displacement
Height: a altura (0 fundo, 1 em cima), Scale: a profundidade
Displacement ligado na entrada Displacement da Material Output
A superfície parece afundar onde a altura é baixa
```
O **parallax occlusion** faz uma superfície plana parecer ter relevo: pedras, tijolos, rejunte afundado. Cada pixel procura, ao longo do olhar, onde o raio encontra o mapa de altura, e lê o material ali.
- No material (**Blend Mode Opaque**), ligue um nó **Displacement** (Shift+A > Vetor) na entrada **Displacement** da **Material Output**. Na **Height** do Displacement vai a altura: 0 no fundo, 1 em cima. A **Scale** é a profundidade (1 = 5% de uma repetição do UV).
- Use a mesma altura num **Bump** ligado na Normal: o parallax dá a profundidade e o Bump dá a luz nos lados das pedras.
- O exemplo **M_ParallaxCobble** faz um calçamento com dois Voronoi (F2 − F1).
- Custa algumas leituras de textura a mais, só nos pixels desse material (cerca de 0,15 ms com metade da tela coberta no Épico).
- **Limites**: a borda da malha continua reta (não recorta a silhueta), e materiais Masked ou translúcidos não fazem parallax.
--- en
```diagram steps
Opaque material: a Displacement node
Height: the height (0 bottom, 1 top), Scale: the depth
Displacement into the Material Output's Displacement input
The surface looks sunk where the height is low
```
**Parallax occlusion** makes a flat surface look like it has depth: stones, bricks, sunken mortar. Each pixel searches along the view for where the ray meets the height map, and reads the material there.
- In the material (**Blend Mode Opaque**), link a **Displacement** node (Shift+A > Vector) into the **Material Output**'s **Displacement** input. The Displacement's **Height** is the height: 0 at the bottom, 1 on top. **Scale** is the depth (1 = 5% of a UV repeat).
- Feed the same height into a **Bump** on the Normal: the parallax gives the depth, the Bump the light on the stones' sides.
- The **M_ParallaxCobble** example makes cobblestones from two Voronoi (F2 − F1).
- It costs a few more texture reads, only on that material's pixels (about 0.15 ms with half the screen covered at Epic).
- **Limits**: the mesh's edge stays straight (no cut silhouette), and Masked or translucent materials don't do parallax.
