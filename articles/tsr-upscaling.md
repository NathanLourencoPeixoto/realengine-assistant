id: tsr-upscaling
kind: concept
title: TSR: resolução menor, imagem nítida | TSR: a lower resolution, a sharp image
keys: tsr, upscaling, upscale, resolucao, super resolution, nitidez, serrilhado, aliasing, temporal, render scale, rastro, ghost, ghosting, borrao, cintilando, modo de upscaling, qualidade equilibrado desempenho, quality balanced performance, resolucao dinamica, dynamic resolution, mip bias
--- pt
```diagram bars fps
heavy, sem TSR (MSAA 4x): 31
heavy, TSR 75%: 65
casa assombrada, sem TSR: 93
casa assombrada, TSR 75%: 147
```
O **TSR** (Temporal Super Resolution) desenha a cena numa resolução menor e reconstrói a imagem final com os quadros anteriores: quase a nitidez da resolução cheia por bem menos GPU (como o TSR da Unreal).
- A fração vem da escalabilidade: Baixo 50%, Médio 60%, Alto 67%, Épico 75%, Cinemático 100%. [Abrir as Configurações do Projeto](open:project)
- **Modo de Upscaling** (Configurações do Projeto > Rendering, e no menu de opções do jogo): Predefinição (a da escalabilidade), Nativo 100%, Qualidade 67%, Equilibrado 58%, Desempenho 50%, Ultra Desempenho 33%. Na cena heavy do Épico: Nativo 47 fps, Qualidade 71, Desempenho 97, Ultra 131.
- **Resolução Dinâmica** (com o FPS alvo): o render diminui quando a GPU não chega no alvo, até metade da parte do modo, e volta a crescer quando sobra. Muda em passos de 5% e só quando o atraso se mantém (cada passo refaz os alvos do render).
- **Upscaler**: o TSR da engine, ou NVIDIA DLSS, AMD FSR e Intel XeSS no lugar dele. [DLSS, FSR e XeSS](article:vendor-upscalers)
- As texturas leem um mip mais fino quanto menor o render (o mip bias): ficam com a nitidez da tela cheia.
- A cada quadro a câmera anda um subpixel (jitter). O TSR junta esses quadros: as bordas ficam lisas sem MSAA.
- O que se move (atores, personagens, **multidões**) entra no passe de velocidade: o histórico acompanha o movimento e não fica rastro.
- **Cintila?** Duas superfícies no mesmo lugar (dois chãos em z 0, por exemplo) brigam pela profundidade, e o jitter mostra isso a cada quadro. Afaste uma delas 1 cm.
- Para comparar: `REALENGINE_NO_TSR=1` desliga, `REALENGINE_TSR_SCALE=0.5` força a fração. Veja [Linha de comando](article:command-line).
- O custo e a cintilação aparecem no Debug Viewer (F10). [Abrir](open:debug)
--- en
```diagram bars fps
heavy, no TSR (MSAA 4x): 31
heavy, TSR 75%: 65
haunted house, no TSR: 93
haunted house, TSR 75%: 147
```
**TSR** (Temporal Super Resolution) draws the scene at a lower resolution and rebuilds the final image from the previous frames: nearly full-resolution sharpness for far less GPU (like Unreal's TSR).
- The share comes from the scalability: Low 50%, Medium 60%, High 67%, Epic 75%, Cinematic 100%. [Open the Project Settings](open:project)
- **Upscaling Mode** (Project Settings > Rendering, and in the game's options menu): Preset (the scalability's), Native 100%, Quality 67%, Balanced 58%, Performance 50%, Ultra Performance 33%. In the heavy scene at Epic: Native 47 fps, Quality 71, Performance 97, Ultra 131.
- **Dynamic Resolution** (with its target FPS): the render shrinks when the GPU can't reach the target, down to half the mode's share, and grows back when there is room. It moves in 5% steps and only when the lag holds (each step remakes the render's targets).
- **Upscaler**: the engine's TSR, or NVIDIA DLSS, AMD FSR and Intel XeSS in its place. [DLSS, FSR and XeSS](article:vendor-upscalers)
- Textures read a finer mip the smaller the render (the mip bias): they keep the full screen's sharpness.
- Each frame the camera shifts by a subpixel (jitter). TSR gathers those frames: edges come out smooth without MSAA.
- What moves (actors, characters, **crowds**) goes into the velocity pass: the history follows the motion and leaves no trail.
- **Flickering?** Two surfaces in one place (two floors at z 0, say) fight for the depth, and the jitter shows it every frame. Move one of them 1 cm.
- To compare: `REALENGINE_NO_TSR=1` turns it off, `REALENGINE_TSR_SCALE=0.5` forces the share. See [Command line](article:command-line).
- The cost and the flicker show in the Debug Viewer (F10). [Open](open:debug)
