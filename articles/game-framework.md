id: game-framework
kind: concept
title: Player Start, Pawn, Character e Game Mode | Player Start, Pawn, Character and Game Mode
keys: player start, onde o jogador nasce, spawn do jogador, pawn, game mode, gamemode, default pawn, qual personagem o jogo usa, jogador nasce no lugar errado
--- pt
```diagram steps
Game Mode escolhe o Pawn | Player Start: onde nasce | Character: o que você controla | A câmera segue
```
- **Player Start**: onde o jogador começa. [Adicionar](add:PlayerStart)
- **Pawn**: algo que o jogador controla. **Character** é um Pawn que anda, pula e tem colisão de cápsula.
- **Game Mode**: as regras do jogo e qual Pawn o jogador recebe (Configurações do Projeto: Default Pawn). [Abrir](open:project)
- Sem Player Start, o jogador começa onde a câmera do editor estava.
--- en
```diagram steps
The Game Mode picks the Pawn | Player Start: where it begins | Character: what you control | The camera follows
```
- **Player Start**: where the player begins. [Add one](add:PlayerStart)
- **Pawn**: something the player controls. **Character** is a Pawn that walks, jumps and has a capsule collision.
- **Game Mode**: the game's rules and which Pawn the player gets (Project Settings: Default Pawn). [Open them](open:project)
- Without a Player Start, the player begins where the editor's camera was.
