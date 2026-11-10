id: dialogue
kind: recipe
title: Diálogo: conversa com NPC, escolhas, condições e ações | Dialogue: NPC conversations, choices, conditions and actions
keys: dialogo, diálogo, dialogue, conversa, conversation, falar, talk, npc, fala, falas, line, lines, legenda, subtitle, escolha, escolhas, choice, choices, opcao, opção, option, options, resposta, reply, arvore de dialogo, dialogue tree, mercador, merchant, loja, shop, quest, missao, missão, condicao, condição, condition, acao, ação, action, dialogue speaker, start dialogue, choose option, skip line, end dialogue, is in dialogue, set dialogue language, on dialogue line, on dialogue choice, on dialogue end, wbp_dialogue, letra a letra, typewriter, texto aparecendo, camera de conversa, conversation camera, idioma do dialogo, espanhol, spanish, traducao, translation, salto, jump, rdlg
--- pt
Um **Diálogo** é um asset (Content Browser > Adicionar > **Diálogo**; o **Exemplo do Mercador** já vem montado) com um grafo de nós: **Início**, **Fala** (quem fala — vazio é o NPC, `Player` é o jogador —, o texto em inglês, português e espanhol, voz, animação ou Montage, esperar o jogador ou uma duração), **Escolha** (mostra as **Opções** ligadas a ela), **Opção** (o que o jogador diz; **Escolher Só Uma Vez** some depois de escolhida), **Saltar para o Nó** e **Fim**.
- Cada nó pode ter **Condições** (Tem a Gameplay Tag, Tem o Item, Variável, Vida, Já Dito; do jogador ou de quem fala) e **Ações** ao passar (Dar Item, Tirar Item, Pôr / Tirar Gameplay Tag, Chamar Custom Event com entradas, Definir Variável, Abrir a Loja).
- A conversa segue a **primeira ligação cujo nó passa** nas condições; uma Escolha mostra **só as Opções que passam** (a condição esconde a opção). Escolha sem texto deixa a última fala (a pergunta) na tela.
- O editor tem a **Prévia**: roda a conversa ali mesmo, com um jogador de mentira (tags, itens, vida) e o idioma escolhido.
- No NPC: **Details > Adicionar > Dialogue Speaker**: o Diálogo, o nome exibido, pausar o jogo, virar para o jogador e a **câmera de conversa**.
- Nós (categoria **Dialogue**): **Start Dialogue** (Target: o NPC), **Choose Option**, **Skip Line**, **End Dialogue**, **Is In Dialogue**, **Set Dialogue Language** ("es", "pt", "en"); eventos **Event On Dialogue Line**, **On Dialogue Choice**, **On Dialogue End**.
- A tela pronta é o **WBP_Dialogue** (Content/UI): nome, texto letra a letra, opções por mouse, teclado (setas + Enter) e controle (direcional + A).
- **Save Game to Slot** guarda o que já foi dito e escolhido.

```diagram steps
Start Dialogue no NPC | Fala aparece letra a letra | Escolha: opções que passam | Opção: ações (item, tag, evento) | Fim: Event On Dialogue End
```
```blueprint
Event Key E -> Start Dialogue ( Target = NPC, Dialogue = "DLG_Merchant" )
Event On Dialogue Choice ( Speaker, Option, Text ) -> Print String ( Text )
Event On Dialogue End ( Speaker, Dialogue ) -> Add Gameplay Tag ( Tag = "Quest.Talked" )
```
```real
class Merchant extends Actor
    event OnTalk()
        StartDialogue("DLG_Merchant")

    event OnDialogueChoice(speaker: Actor, option: int, text: string)
        print("escolheu: " + text)

    event OnDialogueEnd(speaker: Actor, dialogue: string)
        print("fim de " + dialogue)
```
--- en
A **Dialogue** is an asset (Content Browser > Add > **Dialogue**; the **Merchant Example** comes ready) holding a graph of nodes: **Start**, **Line** (who speaks — empty is the NPC, `Player` is the player —, the text in English, Portuguese and Spanish, a voice, an animation or Montage, wait for the player or a duration), **Choice** (shows the **Options** wired to it), **Option** (what the player says; **Choose Only Once** goes away once chosen), **Jump to Node** and **End**.
- Every node may carry **Conditions** (Has Gameplay Tag, Has Item, Variable, Health, Said Before; the player's or the speaker's) and **Actions** run when it is passed (Give Item, Take Item, Add / Remove Gameplay Tag, Call Custom Event with inputs, Set Variable, Open Shop).
- The conversation follows the **first link whose node passes** its conditions; a Choice shows **only the Options that pass** (a condition hides an option). A Choice without text keeps the last line (the question) on the screen.
- The editor has a **Preview**: it runs the conversation right there, with a made-up player (tags, items, health) and the language picked.
- On the NPC: **Details > Add > Dialogue Speaker**: the Dialogue, the name shown, pause the game, face the player and the **conversation camera**.
- Nodes (category **Dialogue**): **Start Dialogue** (Target: the NPC), **Choose Option**, **Skip Line**, **End Dialogue**, **Is In Dialogue**, **Set Dialogue Language** ("es", "pt", "en"); events **Event On Dialogue Line**, **On Dialogue Choice**, **On Dialogue End**.
- The ready screen is **WBP_Dialogue** (Content/UI): the name, the text letter by letter, the options by mouse, keyboard (arrows + Enter) and gamepad (D-pad + A).
- **Save Game to Slot** keeps what was already said and chosen.

```diagram steps
Start Dialogue on the NPC | a Line appears letter by letter | Choice: the Options that pass | Option: actions (item, tag, event) | End: Event On Dialogue End
```
```blueprint
Event Key E -> Start Dialogue ( Target = NPC, Dialogue = "DLG_Merchant" )
Event On Dialogue Choice ( Speaker, Option, Text ) -> Print String ( Text )
Event On Dialogue End ( Speaker, Dialogue ) -> Add Gameplay Tag ( Tag = "Quest.Talked" )
```
```real
class Merchant extends Actor
    event OnTalk()
        StartDialogue("DLG_Merchant")

    event OnDialogueChoice(speaker: Actor, option: int, text: string)
        print("chose: " + text)

    event OnDialogueEnd(speaker: Actor, dialogue: string)
        print("end of " + dialogue)
```
