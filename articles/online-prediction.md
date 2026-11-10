id: online-prediction
kind: concept
title: Testar com vários jogadores e o movimento previsto | Testing with several players and predicted movement
keys: varios jogadores, several players, number of players, numero de jogadores, testar multiplayer no editor, test multiplayer in editor, play as client, play as listen server, listen server, duas janelas, two windows, predicao, prediction, client side prediction, reconciliacao, reconciliation, server authoritative, autoridade do servidor, movimento online, online movement, lag no movimento, rubber banding, personagem voltando, character snapping back, anti cheat movimento
--- pt
```diagram steps
Cliente: anda na hora (previsto) e manda cada movimento ao servidor
Servidor: move o pawn com eles (a autoridade dele) e responde onde ficou
Cliente: igual, nada; diferente, toma o do servidor e refaz os movimentos seguintes
```
**Vários jogadores no Play:** na setinha ao lado do **Play**, **Number of Players** (1 a 4). Com mais de 1, este editor hospeda a sessão (Listen Server) e cada outro jogador abre numa janela própria, que entra sozinha; **Stop** fecha todas. Cada janela é um jogador de verdade, pela rede local, com os mesmos Blueprints e regras.
**O movimento do personagem online** é como o da Unreal: o servidor manda, sem deixar o jogador esperar.
- O seu **Character** anda na hora na sua tela (**predição**); cada movimento (direção, pulo, tempo do quadro) é guardado e vai ao servidor, vários por pacote (um pacote perdido não custa nada).
- O **servidor** move o seu pawn com esses movimentos, na física dele (paredes, plataformas, pulos): ninguém consegue correr mais rápido ou atravessar parede mexendo no próprio jogo.
- Ele responde com o último movimento que aplicou e onde o personagem ficou. Se a sua tela concordar (até 2 cm), nada acontece; se não, a sua posição volta à do servidor e os movimentos que ele ainda não viu são refeitos dali (**reconciliação**), sem o personagem "voltar no tempo".
- Medido com 100 ms de atraso, oscilação e 5% de perda: 1,5 cm de diferença média, correções em menos de 1 de cada 10 confirmações.
- Os veículos e os pawns que não são Character continuam mandando o próprio estado (o servidor confere a velocidade).
--- en
```diagram steps
Client: moves at once (predicted) and sends each move to the server
Server: moves the pawn with them (its authority) and answers where it ended
Client: the same, nothing; different, takes the server's and redoes the moves after it
```
**Several players in Play:** on the small arrow next to **Play**, **Number of Players** (1 to 4). With more than 1, this editor hosts the session (Listen Server) and each other player opens in its own window, which joins by itself; **Stop** closes them all. Each window is a real player, over the local network, with the same Blueprints and rules.
**The character's online movement** works like Unreal's: the server is in charge, without making the player wait.
- Your **Character** moves at once on your screen (**prediction**); each move (direction, jump, frame time) is kept and goes to the server, several per packet (a lost packet costs nothing).
- The **server** moves your pawn with those moves, in its own physics (walls, platforms, jumps): nobody can run faster or go through a wall by tampering with their own game.
- It answers with the last move it applied and where the character ended up. If your screen agrees (within 2 cm), nothing happens; if not, your position goes back to the server's and the moves it hasn't seen yet are redone from there (**reconciliation**), without the character "going back in time".
- Measured with 100 ms of latency, jitter and 5% loss: 1.5 cm of mean difference, corrections in fewer than 1 in 10 confirmations.
- Vehicles and pawns that aren't Characters still send their own state (the server checks the speed).
