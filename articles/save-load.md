id: save-load
kind: recipe
title: Salvar e carregar o jogo | Save and load the game
keys: salvar jogo, carregar jogo, save game, load game, progresso, checkpoint, slot, continuar de onde parou
--- pt
Grava as variáveis do ator num slot e as lê de volta (o jogo empacotado guarda na pasta do usuário).

```blueprint
Event BeginPlay
  -> Branch ( Does Save Game Exist ( "slot1" ) )
       True -> Load Game from Slot ( Target = self, Slot Name = "slot1" )
Ao passar de fase: Save Game to Slot ( Target = self, Slot Name = "slot1" )
```
```real
class Progress extends Actor
    var level_reached = 1

    event BeginPlay()
        if DoesSaveGameExist("slot1")
            LoadGameFromSlot("slot1")
        print("Level {level_reached}")

    event LevelDone()
        level_reached += 1
        SaveGameToSlot("slot1")
```
--- en
Writes the actor's variables to a slot and reads them back (the packaged game keeps them in the user's folder).

```blueprint
Event BeginPlay
  -> Branch ( Does Save Game Exist ( "slot1" ) )
       True -> Load Game from Slot ( Target = self, Slot Name = "slot1" )
On a level done: Save Game to Slot ( Target = self, Slot Name = "slot1" )
```
```real
class Progress extends Actor
    var level_reached = 1

    event BeginPlay()
        if DoesSaveGameExist("slot1")
            LoadGameFromSlot("slot1")
        print("Level {level_reached}")

    event LevelDone()
        level_reached += 1
        SaveGameToSlot("slot1")
```
