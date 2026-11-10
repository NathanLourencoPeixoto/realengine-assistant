id: cinematics-render
kind: howto
title: Renderizar um vídeo e gravar takes (Movie Render Queue, Take Recorder) | Render a video and record takes (Movie Render Queue, Take Recorder)
keys: movie render queue, render queue, renderizar video, render video, exportar video, export video, exportar cinematica, export cinematic, gravar cinematica, render a cutscene, png sequence, sequencia de png, frames, quadros, motion blur, desfoque de movimento, temporal samples, amostras temporais, take recorder, gravar take, record take, gravar o jogo, record gameplay, gravar movimento, fade, fade in, fade out, escurecer a tela, fade to black, tela preta, cinematics, cinematica
--- pt
```diagram steps
Janela > Cinematics
Take Recorder: no Play, Record grava o jogador e os selecionados
Sequencer: trilha Fade (escurece / clareia), cortes de câmera
Movie Render Queue: escolha a sequência e Render: quadros PNG
```
A janela **Cinematics** (menu **Window**) junta dois recursos de cinema da Unreal.
- **Take Recorder:** dê Play (Alt+P), selecione os atores e clique **Record**; o pawn do jogador entra sozinho. **Stop Recording** salva uma Level Sequence nova em `Content/Cinematics/Takes` (Take, Take_1...) com uma chave de Transform a cada quadro do take (**Take Frame Rate**, 30). Abra no Sequencer para cortar, acrescentar câmeras e eventos.
- **Movie Render Queue:** escolha a **Sequence**, o **Frame Rate**, os **Temporal Samples** e clique **Render (PNG)**. A engine entra no Play, espera os **Warm Up Frames** (a exposição e a iluminação se acertarem) e toca a sequência num relógio fixo: cada quadro é a média das suas amostras espalhadas no tempo, o que dá desfoque de movimento e bordas lisas, por mais lento que seja o PC. Os quadros vão para `Saved/MovieRenders/<sequência>/frame_0000.png` (ou a **Output Folder**); a imagem é a do viewport, então ajuste o tamanho dele antes.
- **Fade:** no Sequencer, a trilha **Fade** escurece a tela até a cor da chave (preto por padrão): valor 1 é a tela toda na cor, 0 nada, linear entre as chaves.
- **Custo:** o teste (32 quadros de 2560 x 1360 com 4 amostras) renderiza em ~3 s.
--- en
```diagram steps
Window > Cinematics
Take Recorder: in Play, Record records the player and the selected actors
Sequencer: the Fade track (darken / brighten), camera cuts
Movie Render Queue: pick the sequence and Render: PNG frames
```
The **Cinematics** window (**Window** menu) brings two of Unreal's cinematic tools.
- **Take Recorder:** press Play (Alt+P), select the actors and click **Record**; the player's pawn comes in by itself. **Stop Recording** saves a new Level Sequence in `Content/Cinematics/Takes` (Take, Take_1...) with a Transform key at each frame of the take (**Take Frame Rate**, 30). Open it in the Sequencer to trim it and add cameras and events.
- **Movie Render Queue:** pick the **Sequence**, the **Frame Rate**, the **Temporal Samples** and click **Render (PNG)**. The engine enters Play, waits the **Warm Up Frames** (the exposure and lighting settle) and plays the sequence on a fixed clock: each frame is the mean of its samples spread over its time, which gives motion blur and smooth edges, however slow the PC. The frames go to `Saved/MovieRenders/<sequence>/frame_0000.png` (or the **Output Folder**); the picture is the viewport's, so size it first.
- **Fade:** in the Sequencer, the **Fade** track darkens the screen to the key's color (black by default): 1 is the whole screen in the color, 0 none, linear between keys.
- **Cost:** the test (32 frames of 2560 x 1360 with 4 samples) renders in ~3 s.
