id: tsr-upscaling
kind: concept
title: TSR: resolução menor, imagem nítida | TSR: a lower resolution, a sharp image
keys: tsr, upscaling, upscale, resolucao, super resolution, dlss, fsr, nitidez, serrilhado, aliasing, temporal, render scale, rastro, ghost, ghosting, borrao, cintilando
--- pt
```diagram bars fps
heavy, sem TSR (MSAA 4x): 31
heavy, TSR 75%: 65
casa assombrada, sem TSR: 93
casa assombrada, TSR 75%: 147
```
O **TSR** (Temporal Super Resolution) desenha a cena numa resolução menor e reconstrói a imagem final com os quadros anteriores: quase a nitidez da resolução cheia por bem menos GPU (como o TSR da Unreal).
- A fração vem da escalabilidade: Baixo 50%, Médio 60%, Alto 67%, Épico 75%, Cinemático 100%. [Abrir as Configurações do Projeto](open:project)
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
- Each frame the camera shifts by a subpixel (jitter). TSR gathers those frames: edges come out smooth without MSAA.
- What moves (actors, characters, **crowds**) goes into the velocity pass: the history follows the motion and leaves no trail.
- **Flickering?** Two surfaces in one place (two floors at z 0, say) fight for the depth, and the jitter shows it every frame. Move one of them 1 cm.
- To compare: `REALENGINE_NO_TSR=1` turns it off, `REALENGINE_TSR_SCALE=0.5` forces the share. See [Command line](article:command-line).
- The cost and the flicker show in the Debug Viewer (F10). [Open](open:debug)
