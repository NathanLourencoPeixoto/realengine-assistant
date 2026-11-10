id: sequencer
kind: howto
title: Cutscenes com o Sequencer | Cutscenes with the Sequencer
keys: cutscene, cinematica, sequencer, camera animada, trailer, cena, sequencia, keyframe, linha do tempo, editor de curvas, curve editor, interpolacao, interpolation, tangente, tangent, auto key, chave automatica, criar camera, create camera, actor to sequencer, intervalo de reproducao, playback range, copiar chaves, tocar para tras
--- pt
```diagram steps
Adicionar > Level Sequence | + Trilha > Ator para o Sequencer (ou arraste do Organizador) | Chaves na linha do tempo, curvas no Editor de Curvas | Play Sequence no jogo
```
1. Navegador: **Adicionar > Level Sequence**; duplo clique abre o Sequencer (o layout do da Unreal).
2. **+ Trilha > Ator para o Sequencer** (ou arraste um ator do Organizador para a lista): o ator vira um grupo com a Transformação; o **+ Trilha** do grupo adiciona Visibilidade, Luz, Campo de Visão, Animação, Áudio e Evento. Trilhas mestre: Cortes de Câmera, Evento, Áudio e Fade.
3. **Criar Câmera**: uma câmera onde o viewport olha, já vinculada e com o corte dela no cursor de tempo.
4. Chaves: o ◆ da trilha (ou **S**) cria no cursor de tempo; ◀ ▶ vão para a chave anterior e a próxima; abrindo a Transformação, cada canal (Posição X, Rotação Y...) mostra o valor naquele quadro e editar o valor cria a chave. Com a **Chave Automática** (o ponto vermelho), mover o ator no viewport grava a chave.
5. Selecione chaves com clique (Ctrl / Shift somam) ou uma caixa; arraste para mover; **botão direito > Interpolação**: Auto, Usuário, Linear, Constante; **Ctrl+C / Ctrl+V** copiam para o cursor; **Del** apaga; **Ctrl+Z / Ctrl+Y** desfazem e refazem.
6. **Editor de Curvas** (aba embaixo): as curvas da trilha selecionada; arraste as chaves (tempo e valor) e as alças das tangentes; **F** enquadra.
7. O intervalo de reprodução: arraste o início verde e o fim vermelho na régua. Tocar para frente ou para trás, repetir, quadros (Esquerda / Direita).
8. No jogo: o nó **Play Sequence** (e **Stop Sequence**).
--- en
```diagram steps
Add > Level Sequence | + Track > Actor To Sequencer (or drag from the Outliner) | Keys on the timeline, curves in the Curve Editor | Play Sequence in the game
```
1. Browser: **Add > Level Sequence**; double-click opens the Sequencer (Unreal's layout).
2. **+ Track > Actor To Sequencer** (or drag an actor from the Outliner onto the list): the actor becomes a group with its Transform; the group's **+ Track** adds Visibility, Light, Field Of View, Animation, Audio and Event. Master tracks: Camera Cuts, Event, Audio and Fade.
3. **Create Camera**: a camera where the viewport looks, already bound with its cut at the playhead.
4. Keys: the track's ◆ (or **S**) keys at the playhead; ◀ ▶ jump to the previous and next key; opening the Transform, each channel (Location X, Rotation Y...) shows its value at that frame and editing it keys it. With **Auto Key** (the red dot), moving the actor in the viewport keys it.
5. Select keys by clicking (Ctrl / Shift add) or with a box; drag to move; **right click > Interpolation**: Auto, User, Linear, Constant; **Ctrl+C / Ctrl+V** copy to the playhead; **Del** deletes; **Ctrl+Z / Ctrl+Y** undo and redo.
6. **Curve Editor** (the bottom tab): the selected track's curves; drag the keys (time and value) and the tangents' handles; **F** frames them.
7. The playback range: drag the green start and the red end on the ruler. Play forward or backwards, loop, step frames (Left / Right).
8. In the game: the **Play Sequence** node (and **Stop Sequence**).
