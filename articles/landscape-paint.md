id: landscape-paint
kind: howto
title: Pintar camadas no Landscape (grama, terra, pedra) | Paint layers on the Landscape (grass, dirt, rock)
keys: pintar landscape, paint landscape, pintar terreno, paint terrain, camadas do terreno, landscape layers, weightmap, weight map, landscape layer blend, layer blend, terra e grama, grass and dirt, caminho no terreno, path on terrain, textura do terreno, terrain texture, misturar materiais, blend materials, desfazer escultura, undo sculpt, exportar heightmap, export heightmap, r16
--- pt
```diagram steps
Material do Landscape: Details > Landscape Layers: 3 materiais e o Tile
Modo Landscape (Shift+2): Paint, escolha a Layer
Pinte no viewport (Shift: Erase); Ctrl+Z desfaz o traço
Export Heightmap (.r16): as alturas para outro programa
```
O Landscape mistura até **quatro materiais** pintados à mão (como o Landscape Layer Blend da Unreal): o material do Landscape é a base, e três outros entram onde você pinta.
- **As camadas:** abra o material do Landscape e, em **Details > Landscape Layers**, arraste três materiais (**Layer 1, 2, 3**) e o **Tile** de cada um (cm por repetição, sobre o chão do mundo: não estica nas encostas).
- **Pintar:** no modo **Landscape** (Shift+2), clique **Paint**, escolha a **Layer** (1 a 3) e pinte no viewport; **Shift** troca para **Erase**. **Brush Radius** e **Brush Strength** como na escultura. Uma camada pintada empurra as outras: as fatias somam no máximo 100%, o resto é a base.
- **Desfazer:** **Ctrl+Z** no modo Landscape desfaz o último traço (escultura ou pintura; 8 guardados).
- **Exportar:** **Export Heightmap (.r16)** nos Details grava as alturas em `Content/Landscapes/<nome>.r16` (16 bits: o ponto mais baixo preto, o mais alto branco), para abrir no World Machine, Gaea ou noutro Landscape.
- **Custo:** as camadas leem as texturas só onde há tinta; o teste (200 m, três manchas) gasta +0,4 ms de GPU.
- **Onde fica:** os pesos ficam em `Content/Landscapes/<nome>.rlw` e vão nas cores de vértice dos blocos.
--- en
```diagram steps
The Landscape's material: Details > Landscape Layers: 3 materials and the Tile
Landscape mode (Shift+2): Paint, pick the Layer
Paint in the viewport (Shift: Erase); Ctrl+Z undoes the stroke
Export Heightmap (.r16): the heights for another program
```
The Landscape blends up to **four materials** painted by hand (like Unreal's Landscape Layer Blend): the Landscape's material is the base, and three others come in where you paint.
- **The layers:** open the Landscape's material and, in **Details > Landscape Layers**, drag three materials (**Layer 1, 2, 3**) and each one's **Tile** (cm per repeat, over the world's ground: no stretching on slopes).
- **Paint:** in **Landscape** mode (Shift+2), click **Paint**, pick the **Layer** (1 to 3) and paint in the viewport; **Shift** switches to **Erase**. **Brush Radius** and **Brush Strength** as when sculpting. A painted layer pushes the others aside: the shares add up to 100% at most, the rest is the base.
- **Undo:** **Ctrl+Z** in Landscape mode undoes the last stroke (sculpting or painting; 8 kept).
- **Export:** **Export Heightmap (.r16)** in the Details writes the heights to `Content/Landscapes/<name>.r16` (16 bits: the lowest point black, the highest white), to open in World Machine, Gaea or another Landscape.
- **Cost:** the layers read their textures only where there is paint; the test (200 m, three patches) spends +0.4 ms of GPU.
- **Where it lives:** the weights are in `Content/Landscapes/<name>.rlw` and go into the chunks' vertex colors.
