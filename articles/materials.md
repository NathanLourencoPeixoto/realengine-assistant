id: materials
kind: howto
title: Materiais: criar e aplicar | Materials: make and apply
keys: material, textura, cor, aplicar material, trocar cor, nodes, shader, pbr, metal, rugosidade, material instance
--- pt
1. No Navegador de Conteúdo: **Adicionar > Material**. Duplo clique abre o editor de nós (os nós do Blender: Principled BSDF, Image Texture...).
2. **Arraste o material** do Navegador para uma malha no viewport: ela passa a usá-lo.
3. Para variações sem refazer o grafo, crie uma **Material Instance** e mude só os parâmetros.

As mudanças são compiladas em segundo plano (o cartão "Compilando materiais"); as imagens grandes são lidas fora da thread do editor.
--- en
1. In the Content Browser: **Add > Material**. Double-click opens the node editor (Blender's nodes: Principled BSDF, Image Texture...).
2. **Drag the material** from the Browser onto a mesh in the viewport: it uses it from then on.
3. For variations without redoing the graph, make a **Material Instance** and change only its parameters.

The changes compile in the background (the "Compiling materials" card); big images are read off the editor's thread.
