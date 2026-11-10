id: hdr10-output
kind: howto
title: Saída HDR10 no jogo | HDR10 output in the game
keys: hdr, hdr10, saida hdr, hdr output, monitor hdr, tela hdr, hdr display, st2084, pq, bt2020, rec2020, paper white, branco de papel, pico de brilho, peak brightness, nits, brilho alto, highlights, hdr no windows
--- pt
```diagram steps
Project Settings > Platforms: ligue HDR Output (HDR10)
Ajuste Paper White (o branco da interface e do papel, ~200 nits) e Peak Brightness (o pico da tela, ~1000)
Empacote o jogo: numa tela HDR (com o HDR do Windows ligado) ele abre em HDR10; senão, em SDR
```
Com **HDR Output**, o jogo empacotado usa a tela HDR do jogador: 10 bits por canal, cores BT.2020 e o código PQ (ST.2084).
- **A imagem:** o que era branco no SDR fica no **Paper White**. As partes mais claras que o branco (sol, lâmpadas, reflexos) sobem até o **Peak Brightness**, e os tons médios ficam iguais aos do SDR.
- **A interface** (UMG, menus, HUD) é desenhada à parte e colocada por cima no Paper White, com as cores que você escolheu.
- **Sem tela HDR** (ou com o HDR do Windows desligado), o jogo segue em SDR e escreve no log "HDR10 output: unavailable on this display".
- A intro e a tela de carregamento continuam em SDR; o HDR10 liga depois delas.
- O editor fica em SDR, como o da Unreal.
--- en
```diagram steps
Project Settings > Platforms: turn on HDR Output (HDR10)
Set Paper White (the UI's and paper's white, ~200 nits) and Peak Brightness (the display's peak, ~1000)
Package the game: on an HDR display (with Windows HDR on) it opens in HDR10; otherwise in SDR
```
With **HDR Output**, the packaged game uses the player's HDR display: 10 bits per channel, BT.2020 colors and the PQ code (ST.2084).
- **The picture:** what was white in SDR sits at **Paper White**. The parts brighter than white (sun, lamps, reflections) rise up to **Peak Brightness**, and the mid tones stay the same as in SDR.
- **The UI** (UMG, menus, HUD) is drawn separately and laid on top at Paper White, with the colors you chose.
- **Without an HDR display** (or with Windows HDR off), the game stays in SDR and logs "HDR10 output: unavailable on this display".
- The intro and the loading screen stay in SDR; HDR10 turns on after them.
- The editor stays in SDR, like Unreal's.
