id: gpu-passes
kind: howto
title: GPU por passe e personagens de perto (otimização) | GPU per pass and close characters (optimization)
keys: stat gpu, profilegpu, gpu passes, passes da gpu, custo por passe, gargalo da gpu, fps cai perto do personagem, chegar perto cai o fps, personagem perto pesado, close up lento, lod de personagem, lod skeletal mesh, ray tracing lod, checkerboard, xadrez, denoiser lento, video realista lento, fotorrealista lento, gpu-passes
--- pt
```diagram steps
F10 > GPU Passes | O passe mais caro em cima | Mexa só nele | Meça de novo (--gpu-passes)
```
## Onde a GPU gasta (como o `stat gpu` da Unreal)
- **F10 > GPU Passes** lista cada passe do quadro com o tempo dele: nuvens, neblina, TLAS, GI, sombras, pré-passe, malhas, céu, denoiser, TSR, pós. Só mede com a janela aberta; fechada, não custa nada. [Abrir](open:debug)
- Na linha de comando: `--bench 5 --gpu-passes` imprime a mesma tabela, do mais caro ao mais barato.
- Um sistema novo aparece sozinho na lista com um `gpu_mark(cmd, "nome")` antes do passe dele.
## Chegar perto de um personagem derrubava o FPS
- Perto, o personagem cobre a tela e **cada pixel dele dispara raios** (sombras, reflexo; no Fotorrealista e no Vídeo-realista também a GI). O custo cresce com a área na tela, não com o número de objetos.
- **LODs automáticos para Skeletal Mesh:** a engine simplifica a malha sobre os mesmos vértices (o skinning não muda) e guarda o resultado em cache. Longe, desenha menos triângulos.
- **Ray tracing no LOD 1:** os raios veem o LOD 1 do personagem (um quarto dos triângulos), como o *ray tracing LOD bias* da Unreal. Com o tigre de 309 mil triângulos colado na câmera: −1 ms no Realista e −3 ms no Vídeo-realista. `REALENGINE_SKIN_RT_LOD=0` volta ao LOD 0.
- **Checkerboard do denoiser** (Fotorrealista e Vídeo-realista, Baixo a Épico): cada pixel traça um raio de GI por quadro, difuso ou especular, alternando em xadrez; o denoiser completa o outro pelos vizinhos (como o ReBLUR da NVIDIA). O Cinemático traça os dois.
- **Raios da GI fora do passe principal** (Fotorrealista e Vídeo-realista): o passe principal só anota o que cada pixel precisa e um passe próprio traça os raios depois, com a GPU mais livre. No MyProject, Vídeo-realista Épico a 1440p nativo: 45 → 65 fps.
- Dica de asset: um personagem herói de jogo fica bem com 50 a 150 mil triângulos; acima disso, simplifique antes de importar.
- Veja também: [Debug Viewer](article:debug-viewer), [Orçamento do quadro](article:performance-budget), [Denoiser de RT](article:rt-denoiser).
--- en
```diagram steps
F10 > GPU Passes | The costliest pass on top | Work on that one only | Measure again (--gpu-passes)
```
## Where the GPU spends (like Unreal's `stat gpu`)
- **F10 > GPU Passes** lists every pass of the frame with its time: clouds, fog, TLAS, GI, shadows, prepass, meshes, sky, denoiser, TSR, post. It measures only while the window is open; closed, it costs nothing. [Open](open:debug)
- On the command line: `--bench 5 --gpu-passes` prints the same table, costliest first.
- A new system shows up in the list by itself with a `gpu_mark(cmd, "name")` before its pass.
## Getting close to a character dropped the FPS
- Close up, the character covers the screen and **each of its pixels casts rays** (shadows, reflection; in Photoreal and Video-realistic the GI too). The cost grows with its screen area, not with the object count.
- **Automatic LODs for Skeletal Meshes:** the engine simplifies the mesh over the same vertices (skinning unchanged) and caches the result. Far away it draws fewer triangles.
- **Ray tracing on LOD 1:** the rays see the character's LOD 1 (a quarter of the triangles), like Unreal's *ray tracing LOD bias*. With the 309 thousand triangle tiger against the camera: −1 ms in Realistic and −3 ms in Video-realistic. `REALENGINE_SKIN_RT_LOD=0` goes back to LOD 0.
- **Denoiser checkerboard** (Photoreal and Video-realistic, Low to Epic): each pixel traces one GI ray a frame, diffuse or specular, alternating in a checkerboard; the denoiser fills the other from the neighbors (like NVIDIA's ReBLUR). Cinematic traces both.
- **GI rays out of the main pass** (Photoreal and Video-realistic): the main pass only notes what each pixel needs and a pass of its own traces the rays afterwards, with the GPU freer. In MyProject, Video-realistic Epic at native 1440p: 45 → 65 fps.
- Asset tip: a game hero character is fine with 50 to 150 thousand triangles; above that, simplify it before importing.
- See also: [Debug Viewer](article:debug-viewer), [Frame budget](article:performance-budget), [RT denoiser](article:rt-denoiser).
