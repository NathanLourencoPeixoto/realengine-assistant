id: volumes-vdb
kind: concept
title: Fumaça e explosões de arquivo (OpenVDB) | Smoke and explosions from files (OpenVDB)
keys: vdb, openvdb, .vdb, volume, volume heterogeneo, heterogeneous volume, fumaca simulada, importar fumaca, fumaca vdb, explosao, explosion, embergen, houdini, blender smoke, fumaca do blender, cache de fumaca, smoke cache, sequencia vdb, vdb sequence, fogo do blender, fire from blender
--- pt
```diagram steps
Simule no Tlender, no Blender, no EmberGen ou no Houdini
Exporte .vdb (uma sequência: fumaca_0001.vdb, 0002...)
Adicionar > Efeitos Visuais > Heterogeneous Volume, aponte o File e Frames
A engine toca a sequência e desenha como o fogo dela
```
O **Heterogeneous Volume** (como o da Unreal) toca **fumaça, fogo e explosões** simulados fora da engine, em arquivos **OpenVDB**.
- **Como usar:** ponha os `.vdb` em `Content/Volumes/`, **Adicionar > Efeitos Visuais > Heterogeneous Volume**, escreva o primeiro arquivo em **File** e o número de quadros em **Frames** (1: um arquivo só). **Frame Rate** e **Loop** controlam a reprodução.
- **Grades:** `density` vira fumaça; `temperature` (em kelvin, ou ×**Temperature Scale**) ou `flame` (×**Flame Temperature**) vira a luz do fogo.
- **Eixos:** **Up Axis** Z (Blender, Tlender) ou Y (Houdini, EmberGen); **Unit** em cm por unidade (100: metros).
- **Aparência:** **Density** (quão escura e opaca), **Brightness** (a chama), **Smoke Albedo** (fuligem ... vapor). O sol faz sombra dentro da fumaça.
- **Qualidade:** **Resolution** (células no lado maior). Carrega tudo ao abrir.
- **Exemplo:** `Volumes/Example_Puff_0001.vdb` (24 quadros; cena de teste `volume`).
--- en
```diagram steps
Simulate in the Tlender, Blender, EmberGen or Houdini
Export .vdb (a sequence: smoke_0001.vdb, 0002...)
Add > Visual Effects > Heterogeneous Volume, point File and Frames
The engine plays the sequence and draws it as its own fire
```
A **Heterogeneous Volume** (like Unreal's) plays **smoke, fire and explosions** simulated outside the engine, from **OpenVDB** files.
- **How to use:** put the `.vdb` files in `Content/Volumes/`, **Add > Visual Effects > Heterogeneous Volume**, type the first file in **File** and the frame count in **Frames** (1: a single file). **Frame Rate** and **Loop** drive the playback.
- **Grids:** `density` becomes smoke; `temperature` (in kelvin, or ×**Temperature Scale**) or `flame` (×**Flame Temperature**) becomes the fire's light.
- **Axes:** **Up Axis** Z (Blender, Tlender) or Y (Houdini, EmberGen); **Unit** in cm per unit (100: meters).
- **Look:** **Density** (how dark and thick), **Brightness** (the flame), **Smoke Albedo** (soot ... steam). The sun casts its shadow inside the smoke.
- **Quality:** **Resolution** (cells along the longest side). Everything loads when it opens.
- **Example:** `Volumes/Example_Puff_0001.vdb` (24 frames; test scene `volume`).
