id: interaction
kind: recipe
title: Interação: aperte E para abrir, porta, baú, alavanca, botão | Interaction: press E to use, door, chest, lever, button
keys: interacao, interação, interagir, interact, interaction, interactable, interagivel, interator, interactor, aperte e, press e, tecla e, e para abrir, abrir porta, open door, porta, door, porta trancada, locked door, chave, key, destrancar, unlock, bau, baú, chest, abrir bau, open chest, alavanca, lever, botao, button, apertar botao, press button, interruptor, switch, ligar outro ator, segurar, segurar tecla, hold, hold to interact, barra de segurar, prompt, aviso na tela, texto de interacao, dica de tecla, mostrar tecla, contorno, outline, destaque, highlight, brilho, glow, foco, focus, olhar para, look at, falar com npc, talk to, pegar objeto, use object, on interact, on focus begin, on focus end, on hold progress, get focused interactable, set interaction enabled, set prompt text, get interaction prompt, set device active, is device active, wbp_interactprompt, gamepad, controle
--- pt
O "aperte **E** para usar" de todo jogo, pronto e reaproveitável:
1. Em qualquer ator: **Details > Adicionar > Interagível** (no Blueprint: **Componentes > + Adicionar > Jogabilidade**). Nele: **Texto do Aviso** (`Abrir {0}`, `Falar com {0}`; `{0}` é o **Nome de Exibição**; vazio: o verbo do dispositivo), **Alcance**, **Ângulo de Visão**, **Tecla** ou **Ação de Entrada** (Enhanced Input), **Tempo Segurando** (segurar X s, com barra), **Pode Repetir** (ou uma vez só), **Prioridade** e a **Condição**: uma **Tag Exigida** (`Item.Key.Red`) num item do **Inventário** de quem usa ou nas **Gameplay Tags** dele (com **Gastar o Item** a chave é consumida).
2. O personagem do jogador ganha um **Interator** sozinho no Play: ele acha o melhor interagível pelo raio da câmera e pela distância, não enxerga através de parede, contorna (ou faz brilhar) o ator em foco e mostra o **WBP_InteractPrompt** (tecla + texto + barra de segurar; a tecla vira **X** quando o controle foi o último usado). O widget fica em **Content/UI**: copie e mude.
3. **Atores prontos** (Place Actors ou o menu rápido > Jogabilidade): **Porta** (gira na dobradiça, para longe de quem abre, ou desliza; trancada por chave com a Tag Exigida), **Baú** (abre a tampa e dá os **Itens do Baú** para o inventário de quem abriu), **Alavanca** e **Botão** (ligam e desligam o **Ator Alvo**: uma porta abre, uma luz apaga, um ator some; ou chamam um **Evento Personalizado** nele com a entrada `On`).
4. Eventos do ator: **Event On Interact** (Instigator), **Event On Focus Begin** / **On Focus End**, **Event On Hold Progress** (Progress 0-1). Nós: **Interact**, **Get Focused Interactable**, **Set Interaction Enabled**, **Set Prompt Text**, **Get Interaction Prompt**, **Set Device Active**, **Is Device Active**.

```diagram steps
O Interator olha (raio da câmera + perto) | foco: contorno e aviso na tela | E (ou segurar) | a condição (chave no inventário?) | Event On Interact; a porta abre
```
```blueprint
Event On Focus Begin ( Instigator ) -> Print String ( "olhando para a alavanca" )
Event On Interact ( Instigator ) -> Set Device Active ( Target = Portao, Active = true ) -> Set Interaction Enabled ( Enabled = false )
Event On Hold Progress ( Progress ) -> Print String ( Format Text ( "{0}%", Progress ) )
Event BeginPlay -> Set Prompt Text ( Prompt Text = "Falar com {0}" )
```
```real
class Npc extends Actor
    event BeginPlay()
        SetPromptText("Falar com {0}")

    event OnFocusBegin(instigator: Actor)
        print("o jogador me olhou")

    event OnInteract(instigator: Actor)
        print("Olá, viajante!")
        SetInteractionEnabled(false)

    event OnHoldProgress(progress: float, instigator: Actor)
        print("segurando: {progress}")
```

O custo: o Interator com 200 interagíveis no nível custa ~0,01 ms por quadro; a lista **Interaction** do Debug Viewer (F10) mostra o tempo e o estado de cada um. Para uma chave, veja [Inventário](article:inventory).
--- en
Every game's "press **E** to use", ready and reusable:
1. On any actor: **Details > Add > Interactable** (in a Blueprint: **Components > + Add > Gameplay**). On it: **Prompt Text** (`Open {0}`, `Talk to {0}`; `{0}` is the **Display Name**; empty: the device's verb), **Range**, **View Angle**, **Key** or **Input Action** (Enhanced Input), **Hold Time** (hold X s, with a bar), **Can Repeat** (or once only), **Priority** and the **Condition**: a **Required Tag** (`Item.Key.Red`) on an item in the user's **Inventory** or in its **Gameplay Tags** (with **Consume Item** the key is spent).
2. The player's pawn gets an **Interactor** by itself in Play: it finds the best Interactable by the camera's ray and how near it is, doesn't see through walls, outlines (or makes glow) the actor in focus and shows **WBP_InteractPrompt** (key + text + hold bar; the key becomes **X** when the gamepad was used last). The widget lives in **Content/UI**: copy it and change it.
3. **Ready-made actors** (Place Actors or the quick menu > Gameplay): **Door** (swings on its hinge, away from who opens it, or slides; locked by a key with the Required Tag), **Treasure Chest** (lifts its lid and gives its **Chest Items** to the opener's inventory), **Lever** and **Button** (switch the **Target Actor**: a door opens, a light goes off, an actor hides; or call a **Custom Event** on it with the input `On`).
4. The actor's events: **Event On Interact** (Instigator), **Event On Focus Begin** / **On Focus End**, **Event On Hold Progress** (Progress 0-1). Nodes: **Interact**, **Get Focused Interactable**, **Set Interaction Enabled**, **Set Prompt Text**, **Get Interaction Prompt**, **Set Device Active**, **Is Device Active**.

```diagram steps
The Interactor looks (camera ray + near) | focus: outline and the prompt on screen | E (or hold) | the condition (key in the inventory?) | Event On Interact; the door opens
```
```blueprint
Event On Focus Begin ( Instigator ) -> Print String ( "looking at the lever" )
Event On Interact ( Instigator ) -> Set Device Active ( Target = Gate, Active = true ) -> Set Interaction Enabled ( Enabled = false )
Event On Hold Progress ( Progress ) -> Print String ( Format Text ( "{0}%", Progress ) )
Event BeginPlay -> Set Prompt Text ( Prompt Text = "Talk to {0}" )
```
```real
class Npc extends Actor
    event BeginPlay()
        SetPromptText("Talk to {0}")

    event OnFocusBegin(instigator: Actor)
        print("the player looked at me")

    event OnInteract(instigator: Actor)
        print("Hello, traveler!")
        SetInteractionEnabled(false)

    event OnHoldProgress(progress: float, instigator: Actor)
        print("holding: {progress}")
```

The cost: the Interactor with 200 Interactables in the level takes ~0.01 ms a frame; the Debug Viewer's (F10) **Interaction** list shows the time and the state of each one. For a key, see [Inventory](article:inventory).
