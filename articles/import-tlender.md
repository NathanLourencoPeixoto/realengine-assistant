id: import-tlender
kind: howto
title: Importar do Tlender, OBJ, glTF e FBX | Import from the Tlender, OBJ, glTF and FBX
keys: importar, import, tlender, tlend, obj, fbx, gltf, glb, modelo 3d, blender, personagem importado, arrastar arquivo
--- pt
```diagram steps
Arquivo > Importar (ou arrastar o arquivo) | Opções: Colocar no Nível | Roda em segundo plano (cartão) | Malhas, materiais e animações prontos
```
## Como importar
1. **Arquivo > Importar para o Nível...** ou arraste os arquivos do Explorer para o editor. [Mostrar onde](show:File>Import Into Level...)
2. Na janela de opções, marque **Colocar no Nível** para os objetos aparecerem onde estavam no arquivo.
3. A importação roda em segundo plano: o editor não trava, e um cartão no canto inferior direito mostra o progresso.

## O que vira o quê
- Malhas viram **Static Meshes**; materiais são refeitos pelos nós (os mesmos do Blender).
- Uma armature com a malha que ela deforma vira **Skeletal Mesh**; cada action vira uma **animação**.
- Luzes e câmeras do glTF e do FBX viram atores.
- Cada Static Mesh guarda o **material da importação**: o visualizador da malha mostra com as texturas, a malha arrastada do Content Browser para o nível já vem com ele, e a miniatura ganha a cor dele.

--- en
```diagram steps
File > Import (or drag the file) | Options: Place in Level | Runs in the background (a card) | Meshes, materials and animations ready
```
## How to import
1. **File > Import Into Level...** or drag the files from Explorer into the editor. [Show me where](show:File>Import Into Level...)
2. In the options window, check **Place in Level** to have the objects where they were in the file.
3. The import runs in the background: the editor doesn't freeze, and a card at the bottom right shows its progress.

## What becomes what
- Meshes become **Static Meshes**; materials are rebuilt from their nodes (Blender's).
- An armature with the mesh it deforms becomes a **Skeletal Mesh**; each action an **animation**.
- glTF's and FBX's lights and cameras become actors.
- Each Static Mesh keeps its **import's material**: the mesh viewer shows it with its textures, the mesh dragged from the Content Browser into the level comes with it, and its thumbnail takes its color.
