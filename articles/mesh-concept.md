id: mesh-concept
kind: concept
title: Malha estática e malha esquelética | Static mesh and skeletal mesh
keys: malha, mesh, modelo 3d, static mesh, skeletal mesh, esqueleto, ossos, rig, armature, diferenca entre malhas, modelo animado
--- pt
```diagram compare
 | Static Mesh | Skeletal Mesh
Esqueleto | não | sim
Se deforma | não | sim
Exemplos | pedra, casa, mesa | personagem, animal
Anima | o ator inteiro | os ossos
```
- **Static Mesh**: um modelo que não se deforma (uma pedra, uma casa, uma mesa). Pode se mover, mas inteiro.
- **Skeletal Mesh**: um modelo com **esqueleto** (ossos) que se deforma com animações (personagens, animais).
- Ambas vêm de importação (Tlender, FBX, glTF, OBJ). [Importar](article:import-tlender)
- Malhas pesadas ganham LODs e clusters sozinhas (o detalhe cai com a distância sem você fazer nada).
--- en
```diagram compare
 | Static Mesh | Skeletal Mesh
Skeleton | no | yes
Deforms | no | yes
Examples | rock, house, table | character, animal
Animates | the whole actor | the bones
```
- **Static Mesh**: a model that doesn't deform (a rock, a house, a table). It can move, but whole.
- **Skeletal Mesh**: a model with a **skeleton** (bones) that deforms with animations (characters, animals).
- Both come from an import (Tlender, FBX, glTF, OBJ). [Import](article:import-tlender)
- Heavy meshes get LODs and clusters by themselves (the detail drops with distance without you doing anything).
