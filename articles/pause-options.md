id: pause-options
kind: recipe
title: Menu de pausa e opções (gráficos, áudio, controles, idioma) | Pause menu and options (graphics, audio, controls, language)
keys: escolher dlss no menu, choose dlss in the options, upscaler no menu de opcoes, pausa, pausar, pause, menu de pausa, pause menu, set game paused, is game paused, pausar o jogo, despausar, continuar, resume, tick when paused, tick quando pausado, opcoes, options, configuracoes, settings, game user settings, game user setting, apply settings, aplicar opcoes, volume, volume da musica, volume geral, master volume, music volume, sfx, efeitos, voz, qualidade, preset, predefinicao, baixo medio alto epico, low medium high epic, resolucao, resolution, tela cheia, fullscreen, janela, windowed, vsync, limite de fps, frame rate limit, escala da resolucao, resolution scale, remapear, remapear tecla, rebind, remap key, trocar tecla, input key selector, seletor de tecla, sensibilidade, sensitivity, inverter y, invert y, idioma do jogo, language, sair do jogo, quit game, menu principal, main menu, wbp_pausemenu, wbp_options, esc pausa, salvar opcoes, gameusersettings.ini
--- pt
Como na Unreal: **Set Game Paused** para o mundo (física, animação, partículas, IA, movimento e os sons do jogo) e a UI continua. As opções do jogador ficam num arquivo (**GameUserSettings.ini**) e voltam quando o jogo abre.
1. Já vem pronto: **Esc** no jogo empacotado (no Play do editor a tecla **P**, porque lá o Esc para o Play) e o **Start** do controle abrem o **WBP_PauseMenu**: Continuar, Opções, Menu Principal, Sair. A engine cria ele e o **WBP_Options** em **Content/UI** na primeira vez: copie e mude como qualquer Widget Blueprint.
2. **Opções**: abas Gráficos (predefinição Baixo/Médio/Alto/Épico, resolução, modo de janela, VSync, limite de fps, escala da resolução, **Upscaler**: TSR, DLSS, FSR ou XeSS, só os instalados no PC do jogador), Áudio (Geral, Música, Efeitos, Voz), Controles (sensibilidade, Inverter Y e cada ação do Enhanced Input: clique na tecla e **pressione a nova**) e Idioma. Funciona com mouse, teclado (setas, Enter) e controle (D-pad, A, B volta).
3. Um widget seu mostra uma opção sem nó nenhum: nos Detalhes, **Game User Setting** (um Slider em MasterVolume, um Combo Box em Scalability, um **Input Key Selector** em Key:IA_Jump).
4. Um ator que precisa andar com o jogo pausado (um relógio do menu, uma câmera): **Details > Blueprint > Tick When Paused**, ou o nó **Set Tickable When Paused**.
5. **Project Settings > Maps & Modes > Pause Menu**: ligar/desligar, o seu próprio widget, a tecla do Play; **Main Menu Map** é o que o botão Menu Principal abre.

```diagram steps
Esc (Play: P) | WBP_PauseMenu: o mundo para | Opções: abas, setas e Enter | Aplicar: GameUserSettings.ini | Próxima vez: as opções voltam
```
```blueprint
Event BeginPlay
  -> Set Game User Setting ( Setting = "MusicVolume", Value = 0.5 )
  -> Remap Action Key ( Action = "IA_Jump", Key = "Space", New Key = "F" )
  -> Apply Settings
Custom Event "Morreu"
  -> Set Game Paused ( Paused = true )
  -> Open Pause Menu
```
```real
class PauseHelper extends Actor
    event BeginPlay()
        SetTickableWhenPaused(true)
        var musica = GetGameUserSetting("MusicVolume")
        if musica > 0.8
            SetGameUserSetting("MusicVolume", 0.5, "")
            ApplySettings()

    event Morreu()
        SetGamePaused(true)
        OpenPauseMenu()

    event Tick(dt: float)
        if IsGamePaused()
            print("pausado")
```

Nós: **Set Game Paused**, **Is Game Paused**, **Set Tickable When Paused**, **Get / Set Game User Setting** (nomes: Scalability, Resolution, WindowMode, VSync, FrameRateLimit, ResolutionScale, MasterVolume, MusicVolume, SFXVolume, VoiceVolume, MouseSensitivity, InvertY, Language, Key:IA_Jump), **Apply Settings** (aplica e salva), **Load Settings**, **Set Settings to Defaults**, **Remap Action Key**, **Get Action Key**, **Open / Close Pause Menu**, **Return to Main Menu**, **Quit Game**. Veja também [Interface do jogo](article:game-ui).
--- en
As in Unreal: **Set Game Paused** stops the world (physics, animation, particles, AI, movement and the game's sounds) and the UI goes on. The player's options are kept in a file (**GameUserSettings.ini**) and come back when the game opens.
1. It comes ready: **Esc** in the packaged game (in the editor's Play the **P** key, because there Esc stops the Play) and a gamepad's **Start** open **WBP_PauseMenu**: Resume, Options, Main Menu, Quit. The engine makes it and **WBP_Options** in **Content/UI** the first time: copy and change them like any Widget Blueprint.
2. **Options**: tabs Graphics (preset Low/Medium/High/Epic, resolution, window mode, VSync, frame rate limit, resolution scale, **Upscaler**: TSR, DLSS, FSR or XeSS, only those installed on the player's PC), Audio (Master, Music, Effects, Voice), Controls (sensitivity, Invert Y and each Enhanced Input action: click its key and **press the new one**) and Language. Works with the mouse, the keyboard (arrows, Enter) and a gamepad (D-pad, A, B goes back).
3. A widget of yours shows an option with no node: in Details, **Game User Setting** (a Slider on MasterVolume, a Combo Box on Scalability, an **Input Key Selector** on Key:IA_Jump).
4. An actor that must go on while paused (a menu's clock, a camera): **Details > Blueprint > Tick When Paused**, or the **Set Tickable When Paused** node.
5. **Project Settings > Maps & Modes > Pause Menu**: on/off, your own widget, the Play's key; **Main Menu Map** is what the Main Menu button opens.

```diagram steps
Esc (Play: P) | WBP_PauseMenu: the world stops | Options: tabs, arrows and Enter | Apply: GameUserSettings.ini | Next time: the options are back
```
```blueprint
Event BeginPlay
  -> Set Game User Setting ( Setting = "MusicVolume", Value = 0.5 )
  -> Remap Action Key ( Action = "IA_Jump", Key = "Space", New Key = "F" )
  -> Apply Settings
Custom Event "Died"
  -> Set Game Paused ( Paused = true )
  -> Open Pause Menu
```
```real
class PauseHelper extends Actor
    event BeginPlay()
        SetTickableWhenPaused(true)
        var music = GetGameUserSetting("MusicVolume")
        if music > 0.8
            SetGameUserSetting("MusicVolume", 0.5, "")
            ApplySettings()

    event Died()
        SetGamePaused(true)
        OpenPauseMenu()

    event Tick(dt: float)
        if IsGamePaused()
            print("paused")
```

Nodes: **Set Game Paused**, **Is Game Paused**, **Set Tickable When Paused**, **Get / Set Game User Setting** (names: Scalability, Resolution, WindowMode, VSync, FrameRateLimit, ResolutionScale, MasterVolume, MusicVolume, SFXVolume, VoiceVolume, MouseSensitivity, InvertY, Language, Key:IA_Jump), **Apply Settings** (applies and saves), **Load Settings**, **Set Settings to Defaults**, **Remap Action Key**, **Get Action Key**, **Open / Close Pause Menu**, **Return to Main Menu**, **Quit Game**. See also [The game's UI](article:game-ui).
