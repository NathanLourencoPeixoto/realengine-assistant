id: save-progress
kind: recipe
title: Salvar e carregar o progresso (slots, checkpoints, auto save) | Save and load the progress (slots, checkpoints, auto save)
keys: salvar, salvar jogo, salvar progresso, save, save game, save progress, carregar, carregar jogo, carregar progresso, load, load game, load progress, continuar, continue, novo jogo, new game, slot, slots, save slot, slot de save, savegame, save game object, create save game object, usavegame, progress save game, saveable, salvavel, salvável, checkpoint, ponto de controle, respawn, renascer, respawn at checkpoint, auto save, autosave, salvamento automatico, salvar automaticamente, miniatura, thumbnail, foto do save, list save slots, get save slot info, does save game exist, delete game in slot, apagar save, tempo de jogo, play time, wbp_saveslots, menu de saves, save corrompido, corrupted save, steam cloud, bau aberto, inimigo morto, porta aberta, destruido, destroyed, persistencia, persistence, on game saved, on game loaded, on checkpoint reached
--- pt
Como o **USaveGame** da Unreal, com o estado do mundo junto: um **Save Progress** guarda o nível, o jogador, os atores marcados e as variáveis do progresso num slot; o **Load Progress** abre o nível do slot e põe tudo de volta.
1. **Variáveis do progresso**: crie uma Blueprint Class com pai **Save Game** (moedas, missões, chefes vencidos) e escolha em **Project Settings > Maps & Modes > Save Game > Save Game Class**. **Get Progress Save Game** devolve o objeto: ele passa de nível para nível e entra em cada save.
2. **O mundo**: **Details > Adicionar > Salvável** num ator. Ele salva a posição, a **Vida**, o **Inventário**, as variáveis marcadas **SaveGame** (Details da variável; nos scripts `@savegame`) e se foi **destruído** (um baú aberto, um inimigo morto, uma porta aberta). Os criados no jogo (Spawn Actor) são criados de novo pela classe. O jogador sempre é salvo.
3. **Slots**: cada um guarda nome, data e hora, tempo de jogo, nível e uma **foto da tela** (do quadro seguinte, sem os widgets). **List Save Slots**, **Get Save Slot Info**, **Does Save Game Exist**, **Delete Game in Slot**, **Get Latest Save Slot** (o Continuar).
4. **Automático**: **Project Settings > Auto Save Interval** (segundos) em **Auto Save Slots** que se revezam, **Auto Save on Level Change**, o nó **Auto Save** num evento seu. O jogador desliga nas Opções (aba Idioma > Salvamento Automático).
5. **Checkpoint**: **Place Actors > Checkpoint** (um volume). O jogador entrando salva no slot dele e vira o ponto de volta; com **Respawn on Death** a morte (Vida em 0) volta ali, com o mundo como estava. **Respawn at Checkpoint** faz isso por nó.
6. **Tela pronta**: **WBP_SaveSlots** (Content/UI): Continuar, Carregar, Novo Jogo, Apagar, com a foto; no modo Salvar, Novo Save e Sobrescrever. O menu de pausa já tem **Salvar Jogo** e **Carregar Jogo**; **Open Save Slots Menu** abre de qualquer lugar (o menu principal).
7. O arquivo tem versão e **checksum**: um save danificado é recusado (Success falso, nada muda) e os saves antigos do Save Game to Slot abrem. Com Steam Cloud ligado (Project Settings > Online) vai para a nuvem também.

```diagram steps
Save Progress: nível, jogador, Salváveis, destruídos, Save Game | Arquivo: versão, checksum, foto | Load Progress: Open Level | Antes do BeginPlay: o mundo de volta | Event On Game Loaded
```
```blueprint
Event BeginPlay
  -> Branch ( Does Save Game Exist ( Slot Name = "Slot1" ) )
  -> Load Progress ( Slot Name = "Slot1" )
Custom Event "PegouMoeda"
  -> Cast To SG_MeuProgresso ( Get Progress Save Game )
  -> Set Moedas ( Moedas + 1 )
  -> Auto Save
Event On Checkpoint Reached ( Checkpoint, Player )
  -> Print String ( "Checkpoint!" )
Event Key F5 -> Save Progress ( Slot Name = "Slot1", Display Name = "Meu Jogo" )
Event Key F9 -> Open Save Slots Menu ( Save Mode = false )
```
```real
class Progresso extends Actor
    @savegame
    var moedas: int = 0

    event BeginPlay()
        SetAutoSaveInterval(300)
        if DoesSaveGameExist("Slot1")
            print("há um jogo salvo: " + GetLatestSaveSlot())

    event PegouMoeda()
        moedas = moedas + 1
        AutoSave()

    event SalvarAgora()
        SaveProgress("Slot1", "Meu Jogo")

    event Continuar()
        LoadProgress(GetLatestSaveSlot())

    event OnGameLoaded(slot: string)
        print("carregado: " + slot)

    event OnCheckpointReached()
        print("checkpoint")
```

Nós: **Create Save Game Object**, **Get / Set Progress Save Game**, **Save Progress**, **Load Progress**, **New Game**, **Auto Save**, **Set Auto Save Interval**, **List Save Slots**, **Get Save Slot Info**, **Get Save Slot Name**, **Get Latest Save Slot**, **Get Current Save Slot**, **Get Play Time**, **Does Save Game Exist**, **Delete Game in Slot**, **Save Game to Slot / Load Game from Slot** (as variáveis de um objeto Save Game ou de um ator), **Respawn at Checkpoint**, **Get Last Checkpoint**, **Set Checkpoint**, **Open Save Slots Menu**; eventos **On Game Saved**, **On Game Loaded**, **On Checkpoint Reached**. Veja também [Vida e dano](article:health-damage), [Inventário](article:inventory) e [Menu de pausa](article:pause-options).
--- en
Like Unreal's **USaveGame**, with the world's state along: a **Save Progress** keeps the level, the player, the marked actors and the progress's variables in a slot; **Load Progress** opens the slot's level and puts everything back.
1. **The progress's variables**: make a Blueprint Class whose parent is **Save Game** (coins, quests, bosses beaten) and pick it in **Project Settings > Maps & Modes > Save Game > Save Game Class**. **Get Progress Save Game** gives the object: it goes from level to level and into every save.
2. **The world**: **Details > Add > Saveable** on an actor. It saves its place, its **Health**, its **Inventory**, its variables marked **SaveGame** (the variable's Details; in scripts `@savegame`) and whether it was **destroyed** (a chest opened, an enemy killed, a door left open). The ones spawned while playing (Spawn Actor) are spawned again by their class. The player is always saved.
3. **Slots**: each keeps a name, the date and time, the play time, the level and a **picture of the screen** (from the next frame, without the widgets). **List Save Slots**, **Get Save Slot Info**, **Does Save Game Exist**, **Delete Game in Slot**, **Get Latest Save Slot** (Continue).
4. **Automatic**: **Project Settings > Auto Save Interval** (seconds) over **Auto Save Slots** taking turns, **Auto Save on Level Change**, the **Auto Save** node on an event of yours. The player turns it off in the Options (the Language tab > Auto Save).
5. **Checkpoint**: **Place Actors > Checkpoint** (a volume). The player walking in saves into its slot and makes it the way back; with **Respawn on Death** dying (Health at 0) comes back there, the world as it was. **Respawn at Checkpoint** does it by node.
6. **A ready screen**: **WBP_SaveSlots** (Content/UI): Continue, Load, New Game, Delete, with the picture; in Save mode, New Save and Overwrite. The pause menu already has **Save Game** and **Load Game**; **Open Save Slots Menu** opens it from anywhere (the main menu).
7. The file has a version and a **checksum**: a damaged save is refused (Success false, nothing changes) and the old Save Game to Slot saves open. With Steam Cloud on (Project Settings > Online) it goes to the cloud too.

```diagram steps
Save Progress: level, player, Saveables, destroyed, Save Game | File: version, checksum, picture | Load Progress: Open Level | Before BeginPlay: the world back | Event On Game Loaded
```
```blueprint
Event BeginPlay
  -> Branch ( Does Save Game Exist ( Slot Name = "Slot1" ) )
  -> Load Progress ( Slot Name = "Slot1" )
Custom Event "GotCoin"
  -> Cast To SG_MyProgress ( Get Progress Save Game )
  -> Set Coins ( Coins + 1 )
  -> Auto Save
Event On Checkpoint Reached ( Checkpoint, Player )
  -> Print String ( "Checkpoint!" )
Event Key F5 -> Save Progress ( Slot Name = "Slot1", Display Name = "My Game" )
Event Key F9 -> Open Save Slots Menu ( Save Mode = false )
```
```real
class Progress extends Actor
    @savegame
    var coins: int = 0

    event BeginPlay()
        SetAutoSaveInterval(300)
        if DoesSaveGameExist("Slot1")
            print("a saved game: " + GetLatestSaveSlot())

    event GotCoin()
        coins = coins + 1
        AutoSave()

    event SaveNow()
        SaveProgress("Slot1", "My Game")

    event ContinueGame()
        LoadProgress(GetLatestSaveSlot())

    event OnGameLoaded(slot: string)
        print("loaded: " + slot)

    event OnCheckpointReached()
        print("checkpoint")
```

Nodes: **Create Save Game Object**, **Get / Set Progress Save Game**, **Save Progress**, **Load Progress**, **New Game**, **Auto Save**, **Set Auto Save Interval**, **List Save Slots**, **Get Save Slot Info**, **Get Save Slot Name**, **Get Latest Save Slot**, **Get Current Save Slot**, **Get Play Time**, **Does Save Game Exist**, **Delete Game in Slot**, **Save Game to Slot / Load Game from Slot** (the variables of a Save Game object or an actor), **Respawn at Checkpoint**, **Get Last Checkpoint**, **Set Checkpoint**, **Open Save Slots Menu**; events **On Game Saved**, **On Game Loaded**, **On Checkpoint Reached**. See also [Health and damage](article:health-damage), [Inventory](article:inventory) and [Pause menu](article:pause-options).
