id: enemy-chase
kind: recipe
title: Inimigo que persegue o jogador | An enemy that chases the player
keys: inimigo, perseguir, seguir jogador, ia, monstro, zumbi, enemy, chase, follow, ai move to, behavior tree, navegacao, correr atras
--- pt
O jeito simples: a cada quadro, se o jogador estiver perto, o inimigo anda até ele (**AI Move To** acha o caminho).

```blueprint
Event Tick
  -> Branch ( Get Distance To( Get Player Character ) < Sight )
       True -> AI Move To ( Pawn = self, Destination = Get Actor Location( Get Player Character ), Acceptance Radius = 80 )
```
```real
class Chaser extends Character
    @editable
    var sight = 1500.0

    event Tick(dt: float)
        var player = GetPlayerCharacter()
        if GetDistanceTo(player) < sight
            AIMoveTo(self, player.GetActorLocation(), 80.0)
```
```py
class ChaserPy(Character):
    sight = 1500.0

    def tick(self, dt: float):
        player = get_player_character()
        if get_distance_to(player) < self.sight:
            ai_move_to(self, player.get_actor_location(), 80.0)
```

Para patrulhar, procurar e atacar, use uma **Behavior Tree** com Blackboard ou o **Real Brain**. Veja [IA a fundo](article:ai-pro).
--- en
The simple way: each frame, if the player is near, the enemy walks to them (**AI Move To** finds the path).

```blueprint
Event Tick
  -> Branch ( Get Distance To( Get Player Character ) < Sight )
       True -> AI Move To ( Pawn = self, Destination = Get Actor Location( Get Player Character ), Acceptance Radius = 80 )
```
```real
class Chaser extends Character
    @editable
    var sight = 1500.0

    event Tick(dt: float)
        var player = GetPlayerCharacter()
        if GetDistanceTo(player) < sight
            AIMoveTo(self, player.GetActorLocation(), 80.0)
```
```py
class ChaserPy(Character):
    sight = 1500.0

    def tick(self, dt: float):
        player = get_player_character()
        if get_distance_to(player) < self.sight:
            ai_move_to(self, player.get_actor_location(), 80.0)
```

To patrol, search and attack, use a **Behavior Tree** with a Blackboard or the **Real Brain**. See [AI in depth](article:ai-pro).
