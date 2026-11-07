id: restart-level
kind: recipe
title: Reiniciar a fase (game over) | Restart the level (game over)
keys: reiniciar, game over, recomecar, perdeu, morreu, tentar de novo, restart level, reload level, abrir nivel, open level, trocar de fase, proxima fase
--- pt
Abrir um nível pelo nome recarrega tudo (o mesmo nível: recomeça; outro: próxima fase).

```blueprint
Quando o jogador morre:
  -> Delay ( 2.0 )
  -> Open Level (by Name) ( Level Name = "Main" )
```
```real
class GameOverZone extends Actor
    @editable
    var level_name = "Main"

    event OnBeginOverlap(other: Actor)
        print("Game over")
        Delay(2.0)
        OpenLevelByName(level_name)
```
--- en
Opening a level by name reloads everything (the same level: restart; another: the next level).

```blueprint
When the player dies:
  -> Delay ( 2.0 )
  -> Open Level (by Name) ( Level Name = "Main" )
```
```real
class GameOverZone extends Actor
    @editable
    var level_name = "Main"

    event OnBeginOverlap(other: Actor)
        print("Game over")
        Delay(2.0)
        OpenLevelByName(level_name)
```
