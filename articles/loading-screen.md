id: loading-screen
kind: howto
title: Tela de carregamento e intro do jogo | The game's loading screen and intro
keys: tela de carregamento, loading, splash, intro, abertura, logo, video de abertura, imagem de abertura, icone do jogo, loading screen
--- pt
```diagram steps
Configurações do Projeto | Empacotamento | Tela de Carregamento: imagem ou vídeo | Empacotar
```
- **Configurações do Projeto > Empacotamento > Tela de Carregamento**: escolha uma imagem (PNG, JPEG, BMP, TGA) ou um **vídeo** (MP4, WMV, MOV, AVI, MKV, WebM, em loop). [Abrir](open:project)
- Um arquivo de fora do projeto é copiado para `Content/Splash` e vai junto no jogo empacotado. Por cima só ficam a barra e o texto do carregamento.
- **Mostrar a Intro da Engine** (mesma página) liga ou desliga a animação da Real Engine antes do seu jogo.
- A intro pula com clique, Esc, Espaço ou Enter.
- Veja também: [Empacotar o jogo](article:package-game).
--- en
```diagram steps
Project Settings | Packaging | Loading Screen: an image or a video | Package
```
- **Project Settings > Packaging > Loading Screen**: pick an image (PNG, JPEG, BMP, TGA) or a **video** (MP4, WMV, MOV, AVI, MKV, WebM, looping). [Open](open:project)
- A file from outside the project is copied to `Content/Splash` and goes with the packaged game. Only the loading bar and text sit on top.
- **Show the Engine Intro** (same page) turns the Real Engine animation before your game on or off.
- The intro skips with a click, Esc, Space or Enter.
- See also: [Package the game](article:package-game).
