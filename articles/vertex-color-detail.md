id: vertex-color-detail
kind: concept
title: Cor por vértice e normal de detalhe | Vertex colors and detail normals
keys: cor por vertice, cor de vertice, vertex color, vertex colors, color attribute, atributo de cor, color_0, pintar vertices, tingir malha, tint mesh, normal de detalhe, detail normal, detail texturing, textura de detalhe, detalhe de perto, close up detail, poros, pores, riscos finos, fine scratches, trama, weave, material de detalhe, detail material, repeticao do detalhe, detail tiling
--- pt
```diagram steps
Importe um glTF com cores por vértice (COLOR_0)
No material: Color Attribute ligado na Base Color do Principled
Details do material > Normal de Detalhe: arraste outro material
Repetição e Força: o detalhe fino visto de perto
```
Duas formas de dar variação a um material sem criar outro:
- **Cor por vértice**: um glTF com `COLOR_0` importa as cores junto com a malha. No material, ligue o nó **Color Attribute** (Shift+A > Entrada) na **Base Color** do Principled, direto ou como o A de um **Mix** no modo Multiplicar. Cada malha fica com as cores dela, no mesmo material.
- O Color Attribute só tem efeito multiplicando a Base Color. Ligado em outro lugar (no Alpha, num fator, em outro nó), ele ganha o **"!" laranja** e conta como branco.
- **Normal de detalhe**: em Details do material (sem nó selecionado) > **Normal de Detalhe**, arraste outro material para **Material de Detalhe**. A normal dele vai por cima da deste, repetida **Repetição** vezes, com a **Força** escolhida. Serve para poros, riscos finos e trama de tecido vistos de perto. O exemplo **M_DetailPlaster** usa o **M_DetailNoise**.
- As duas usam as pipelines RE_EXT: um material sem elas não paga nada.
- **Não aparece?** Se a mesma malha também tem um material Masked, Two Sided ou Translucent, ela toda é desenhada sem esses extras. O Registro de Saída avisa. Use outra malha para o material transparente.
- Exemplos em `Materials/Examples`: **M_VertexColor**, **M_DetailNoise**, **M_DetailPlaster**. [Abrir o Content Browser](open:content)
--- en
```diagram steps
Import a glTF with vertex colors (COLOR_0)
In the material: Color Attribute into the Principled's Base Color
The material's Details > Detail Normal: drag another material in
Tiling and Strength: the fine detail seen up close
```
Two ways to vary a material without making another one:
- **Vertex colors**: a glTF with `COLOR_0` imports its colors with the mesh. In the material, link the **Color Attribute** node (Shift+A > Input) into the Principled's **Base Color**, directly or as the A of a **Mix** in Multiply mode. Each mesh keeps its own colors under one material.
- The Color Attribute only counts multiplying the Base Color. Linked elsewhere (its Alpha, a factor, another node) it gets the **orange "!"** and reads as white.
- **Detail normal**: in the material's Details (no node selected) > **Detail Normal**, drag another material into **Detail Material**. Its normal goes over this one's, repeated **Tiling** times, at the **Strength** you pick: pores, fine scratches, fabric weave seen up close. The **M_DetailPlaster** example uses **M_DetailNoise**.
- Both use the RE_EXT pipelines: a material without them pays nothing.
- **Not showing?** If the same mesh also has a Masked, Two Sided or Translucent material, the whole mesh is drawn without these extras; the Output Log says so. Give the transparent material another mesh.
- Examples in `Materials/Examples`: **M_VertexColor**, **M_DetailNoise**, **M_DetailPlaster**. [Open the Content Browser](open:content)
