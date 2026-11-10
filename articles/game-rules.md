id: game-rules
kind: recipe
title: Regras de jogo: partida, rodadas, pontos, vitória e derrota, vidas, cronômetro | Game Rules: match, rounds, score, win and lose, lives, timer
keys: regras de jogo, regras, game rules, game mode, gamemode, modo de jogo, partida, match, rodada, rodadas, round, rounds, melhor de 3, best of 3, fase, fases, match phase, aguardando, waiting, contagem, contagem regressiva, countdown, 3 2 1, jogando, playing, fim de rodada, round over, fim de jogo, game over, pontos, pontuacao, pontuação, score, placar, scoreboard, pontos por morte, pontos por abate, kill points, matar inimigo da pontos, pontuacao alvo, score target, time, times, equipes, teams, cooperativo, co-op, deathmatch, cada um por si, vitoria, vitória, victory, ganhar, vencer, win, derrota, defeat, perder, lose, game over screen, tela de vitoria, tela de derrota, objetivo, objective, eliminar todos os inimigos, eliminate enemies, matar todos, vidas, lives, vida extra, extra life, respawn, renascer, reaparecer, voltar a vida, player start, checkpoint, invencivel ao renascer, spawn protection, cronometro, cronômetro, timer, tempo, tempo esgotado, time up, tempo limite, time limit, relogio da partida, match timer, pausar cronometro, get match phase, set match phase, start match, end match, add score, get score, get team score, get time remaining, set match timer, get lives, add lives, respawn player, restart match, get match result, on match phase changed, on score changed, on match won, on match lost, on round started, on round ended, on player respawned, on timer expired, wbp_matchhud, wbp_matchend, jogar de novo, play again, multiplayer, replicado, replicated
--- pt
As regras da partida (o Game Mode da Unreal) num componente pronto, configurado no Details:
1. **Place Actors > Game Rules** (ou o menu rápido > Jogabilidade). Também em qualquer classe Blueprint: **Componentes > + Adicionar > Game Rules** — um `BP_GameMode` com ele em **Project Settings > Game Mode** vale para todos os níveis. Uma partida por nível.
2. No Details: **Fases** (Aguardando com **Começar Sozinho** e o **Tempo de Espera**, a **Contagem** 3-2-1, o **Tempo do Fim de Rodada**), **Rodadas** (melhor de N), **Times** (cada um por si, um time cooperativo, 2 a 4 times), **Pontos por Abate** (o On Death da [Vida](article:health-damage): quem matou ganha) e pontos próprios para uma vítima com uma **Tag** (`Enemy.Boss`).
3. **Vitória e derrota**: **Pontuação Alvo**, **Vencer por Eliminação** (todos os atores com a **Tag a Eliminar** mortos), **Perder sem Vidas**, **Perder por Mortes** (morto N vezes), **Quando o Tempo Acabar** (derrota, vitória por sobreviver, mais pontos) e o objetivo manual: o nó **End Match** (Won, Reason).
4. **Vidas e renascer**: **Vidas** (0: infinitas), **Atraso para Renascer**, no **Player Start** mais perto ou **No Último Checkpoint** ([Salvar](article:save-progress)), **Invencível ao Renascer** por N segundos.
5. **Cronômetro**: decrescente a partir do **Tempo Limite da Rodada** ou crescente; espera quando o jogo pausa ([Set Game Paused](article:pause-options)) e com **Set Match Timer** (Paused).
6. Na tela: **WBP_MatchHUD** (tempo, pontos, vidas, rodada, a contagem) e, no Fim de Jogo, **WBP_MatchEnd** (Vitória ou Derrota, o motivo, os pontos, **Jogar de Novo** = Restart Match, **Menu Principal**). Ficam em **Content/UI**: copie e mude.

```diagram steps
Aguardando | Contagem 3, 2, 1 | Jogando: abates dão pontos, o cronômetro corre | Fim de Rodada (alvo, tempo, eliminação, sem vidas) | próxima rodada ou Fim de Jogo: Vitória / Derrota
```
Eventos (em todo Blueprint): **On Match Phase Changed**, **On Score Changed**, **On Match Won**, **On Match Lost**, **On Round Started**, **On Round Ended**, **On Player Respawned**, **On Timer Expired**. Nós: **Get/Set Match Phase**, **Start Match**, **End Match**, **Add Score**, **Get Score**, **Get Team Score**, **Get Time Remaining**, **Set Match Timer**, **Get Lives**, **Add Lives**, **Respawn Player**, **Restart Match**, **Get Match Result**. Target desligado (ou um self que não é jogador): o jogador local; no código `AddScore(25)` é do jogador local, `inimigo.AddScore(25)` de um bot.
```blueprint
Event On Match Won ( Winner, Reason ) -> Print String ( Format Text ( "Vitória: {0}", Reason ) )
Event On Score Changed ( Player, Score ) -> Print String ( Format Text ( "Pontos: {0}", Score ) )
Event On Timer Expired -> Print String ( "Tempo esgotado" )
Event ActorBeginOverlap ( Other Actor ) -> Add Lives ( Lives = 1 ) -> Destroy Actor
Event On Interact ( Instigator ) -> End Match ( Won = true, Reason = "Escapou" )
Event On Round Started ( Round ) -> Print String ( Format Text ( "Rodada {0}", Round ) )
```
```real
class RegrasDaFase extends Actor
    event BeginPlay()
        SetMatchTimer(120, false)

    event OnMatchPhaseChanged(fase: int, anterior: int, nome: string)
        print("fase: " + nome)

    event OnScoreChanged(jogador: Actor, pontos: int, delta: int)
        if pontos >= 50 and GetLives() < 3
            AddLives(1)

    event OnTimerExpired()
        print("acabou o tempo")

    event PegouOuro()
        AddScore(25)

    event Fugiu()
        EndMatch(true, "Escapou")

    event OnMatchLost(vencedor: Actor, motivo: string)
        print("derrota: " + motivo)
```

Online: o servidor decide; a fase, o cronômetro, os pontos e as vidas chegam aos clientes (que disparam os mesmos eventos). O estado da partida vai no **Save Progress**. Custo: ~0,001 ms por quadro com 300 inimigos marcados; a lista **Game Rules** do Debug Viewer (F10) mostra a fase e cada jogador.
--- en
The match's rules (Unreal's Game Mode) in a ready component, set up in the Details:
1. **Place Actors > Game Rules** (or the quick menu > Gameplay). Also in any Blueprint class: **Components > + Add > Game Rules** — a `BP_GameMode` with it in **Project Settings > Game Mode** goes for every level. One match a level.
2. In the Details: **Phases** (Waiting with **Auto Start** and the **Wait Time**, the 3-2-1 **Countdown**, the **Round Over Time**), **Rounds** (best of N), **Teams** (each for themself, one co-op team, 2 to 4 teams), **Kill Points** (the [Health](article:health-damage)'s On Death: the killer scores) and points of their own for a victim with a **Tag** (`Enemy.Boss`).
3. **Win and lose**: **Score Target**, **Win by Elimination** (every actor with the **Eliminate Tag** dead), **Lose Out of Lives**, **Lose by Deaths** (dead N times), **When Time Runs Out** (a defeat, a victory by surviving, the most points) and the manual objective: the **End Match** node (Won, Reason).
4. **Lives and respawn**: **Lives** (0: infinite), **Respawn Delay**, at the nearest **Player Start** or **At the Last Checkpoint** ([Save](article:save-progress)), **Invincible After Respawn** for N seconds.
5. **Clock**: down from the **Round Time Limit** or up; it waits while the game is paused ([Set Game Paused](article:pause-options)) and with **Set Match Timer** (Paused).
6. On screen: **WBP_MatchHUD** (time, score, lives, round, the countdown) and, at Game Over, **WBP_MatchEnd** (Victory or Defeat, why, the score, **Play Again** = Restart Match, **Main Menu**). They live in **Content/UI**: copy them and change them.

```diagram steps
Waiting | Countdown 3, 2, 1 | Playing: kills score, the clock runs | Round Over (target, time, elimination, out of lives) | the next round or Game Over: Victory / Defeat
```
Events (in every Blueprint): **On Match Phase Changed**, **On Score Changed**, **On Match Won**, **On Match Lost**, **On Round Started**, **On Round Ended**, **On Player Respawned**, **On Timer Expired**. Nodes: **Get/Set Match Phase**, **Start Match**, **End Match**, **Add Score**, **Get Score**, **Get Team Score**, **Get Time Remaining**, **Set Match Timer**, **Get Lives**, **Add Lives**, **Respawn Player**, **Restart Match**, **Get Match Result**. Target unconnected (or self that is no player): the local player; in code `AddScore(25)` is the local player's, `enemy.AddScore(25)` a bot's.
```blueprint
Event On Match Won ( Winner, Reason ) -> Print String ( Format Text ( "Victory: {0}", Reason ) )
Event On Score Changed ( Player, Score ) -> Print String ( Format Text ( "Score: {0}", Score ) )
Event On Timer Expired -> Print String ( "Time up" )
Event ActorBeginOverlap ( Other Actor ) -> Add Lives ( Lives = 1 ) -> Destroy Actor
Event On Interact ( Instigator ) -> End Match ( Won = true, Reason = "Escaped" )
Event On Round Started ( Round ) -> Print String ( Format Text ( "Round {0}", Round ) )
```
```real
class LevelRules extends Actor
    event BeginPlay()
        SetMatchTimer(120, false)

    event OnMatchPhaseChanged(phase: int, previous: int, name: string)
        print("phase: " + name)

    event OnScoreChanged(player: Actor, score: int, delta: int)
        if score >= 50 and GetLives() < 3
            AddLives(1)

    event OnTimerExpired()
        print("time is up")

    event GotGold()
        AddScore(25)

    event Escaped()
        EndMatch(true, "Escaped")

    event OnMatchLost(winner: Actor, reason: string)
        print("defeat: " + reason)
```

Online: the server decides; the phase, the clock, the scores and the lives reach the clients (which fire the same events). The match's state goes in **Save Progress**. Cost: ~0.001 ms a frame with 300 tagged enemies; the Debug Viewer's (F10) **Game Rules** list shows the phase and each player.
