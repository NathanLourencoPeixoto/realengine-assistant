id: quests
kind: recipe
title: Missões e objetivos: quest log, ir até, coletar, matar, falar, marcador no HUD | Quests and objectives: quest log, go to, collect, kill, talk, HUD marker
keys: missao, missão, missoes, missões, quest, quests, mission, missions, objetivo, objetivos, objective, objectives, tarefa, task, quest log, diario de missoes, diário de missões, journal, etapa, etapas, stage, stages, recompensa, recompensas, reward, rewards, proxima missao, próxima missão, next quest, quest line, linha de missoes, missao secundaria, side quest, missao principal, main quest, ir ate, ir até, go to, chegar, reach, volume, trigger box, coletar, collect, juntar, gather, matar, kill, matar inimigos, kill enemies, contagem, count, falar com npc, talk to npc, entregar itens, hand in, opcional, optional, condicao, condição, condition, tempo limite, time limit, falhar, fail, rastreador, tracker, quest tracker, marcador, marker, waypoint, seta na borda, distancia, distância, distance, hud, start quest, complete quest, fail quest, advance objective, set objective progress, is quest active, is quest completed, get quest state, get objective progress, track quest, get tracked quest, on quest started, on objective updated, on objective completed, on quest completed, on quest failed, wbp_questtracker, rquest, salvar missao, save quest
--- pt
Uma **Missão** é um asset (Content Browser > Adicionar > **Missão**; o **Exemplo do Amuleto Perdido** já vem com todos os tipos de objetivo) com o título e a descrição em inglês, português e espanhol, **etapas** (uma depois da outra, ou **Etapas ao Mesmo Tempo**) e os **objetivos** de cada etapa:
- **Ir Até** (o nome de um ator ou uma Gameplay Tag nele: entrar na Colisão de um **Trigger Box**, ou chegar ao **Raio**), **Interagir** (um ator com **Interagível**: porta, baú, alavanca), **Coletar** N itens (o **Inventário** do jogador; **Entregar os Itens** os tira ao terminar), **Matar** N (o **On Death** da Vida, pela Gameplay Tag: `Enemy.Wolf` conta `Enemy.Wolf.Grey`), **Falar** (a conversa de um **Diálogo** com o NPC termina) e **Manual** (o seu Blueprint o move).
- Cada objetivo pode ser **Opcional**, ter uma **Tag da Condição** (só conta com a tag no jogador) e um **Ator do Marcador**. A etapa pode ter os **Objetivos em Ordem**.
- **Recompensas**: itens, Gameplay Tags, um **Custom Event** (no ator do Quest Log e no **Alvo do Evento**) e a **Próxima Missão**. **Falha Depois de** X segundos faz a missão falhar sozinha.
- No jogador (ou num Game State): **Details > Adicionar > Diário de Missões (Quest Log)**: as **Missões Iniciais**, **Mostrar o Rastreador** (o **WBP_QuestTracker** em Content/UI: título, etapa e objetivos com a contagem) e **Mostrar Marcadores** (o losango sobre o alvo, ou na borda da tela com uma seta, com a distância).
- Nós (categoria **Quest**): **Start Quest**, **Complete Quest**, **Fail Quest**, **Advance Objective**, **Set Objective Progress**, **Is Quest Active**, **Is Quest Completed**, **Get Quest State**, **Get Objective Progress**, **Track Quest**, **Get Tracked Quest**; eventos **On Quest Started**, **On Objective Updated**, **On Objective Completed**, **On Quest Completed**, **On Quest Failed**.
- O progresso vai junto no **Save Progress** (e no **Save Game to Slot**) e passa de um nível para o outro.

```diagram steps
Start Quest (ou Missão Inicial do Quest Log) | Etapa 1: objetivos contam (ir até, coletar...) | Etapa concluída: a próxima começa | Recompensas: itens, tags, evento | Próxima Missão
```
```blueprint
Event BeginPlay -> Start Quest ( Quest = "Q_LostAmulet" )
Event On Objective Completed ( Quest, Objective, Index ) -> Print String ( Objective )
Event Custom PullLever -> Advance Objective ( Quest = "Q_LostAmulet", Objective = "lever", Amount = 1 )
Event On Quest Completed ( Quest, Quest Log ) -> Add Gameplay Tag ( Tag = "Quest.Done" )
```
```real
class QuestGiver extends Actor
    event BeginPlay()
        StartQuest("Q_LostAmulet")

    event OnObjectiveCompleted(quest: string, objective: string, index: int)
        print("objetivo concluído: " + objective)

    event OnQuestCompleted(quest: string, log: Actor)
        print("missão concluída: " + quest)
```
--- en
A **Quest** is an asset (Content Browser > Add > **Quest**; the **Lost Amulet Example** comes with every kind of objective) holding its title and description in English, Portuguese and Spanish, **stages** (one after another, or **Stages at Once**) and each stage's **objectives**:
- **Go To** (an actor's name or a Gameplay Tag on it: walk into a **Trigger Box**'s Collision, or within the **Radius**), **Interact** (an actor with an **Interactable**: door, chest, lever), **Collect** N items (the player's **Inventory**; **Hand In the Items** takes them when it completes), **Kill** N (Health's **On Death**, by Gameplay Tag: `Enemy.Wolf` counts `Enemy.Wolf.Grey`), **Talk** (a **Dialogue** with the NPC ends) and **Manual** (your Blueprint moves it).
- Every objective may be **Optional**, need a **Condition Tag** (it counts only with the tag on the player) and have a **Marker Actor**. A stage may have its **Objectives in Order**.
- **Rewards**: items, Gameplay Tags, a **Custom Event** (on the Quest Log's actor and on the **Event Target**) and the **Next Quest**. **Fail After** X seconds fails the quest by itself.
- On the player (or a Game State): **Details > Add > Quest Log**: the **Starting Quests**, **Show Quest Tracker** (**WBP_QuestTracker** in Content/UI: the title, the stage and the objectives with their counts) and **Show Markers** (a diamond over the target, or at the screen's edge with an arrow, with the distance).
- Nodes (category **Quest**): **Start Quest**, **Complete Quest**, **Fail Quest**, **Advance Objective**, **Set Objective Progress**, **Is Quest Active**, **Is Quest Completed**, **Get Quest State**, **Get Objective Progress**, **Track Quest**, **Get Tracked Quest**; events **On Quest Started**, **On Objective Updated**, **On Objective Completed**, **On Quest Completed**, **On Quest Failed**.
- The progress goes with **Save Progress** (and **Save Game to Slot**) and carries from one level to the next.

```diagram steps
Start Quest (or the Quest Log's Starting Quest) | Stage 1: the objectives count (go to, collect...) | Stage done: the next one starts | Rewards: items, tags, an event | Next Quest
```
```blueprint
Event BeginPlay -> Start Quest ( Quest = "Q_LostAmulet" )
Event On Objective Completed ( Quest, Objective, Index ) -> Print String ( Objective )
Event Custom PullLever -> Advance Objective ( Quest = "Q_LostAmulet", Objective = "lever", Amount = 1 )
Event On Quest Completed ( Quest, Quest Log ) -> Add Gameplay Tag ( Tag = "Quest.Done" )
```
```real
class QuestGiver extends Actor
    event BeginPlay()
        StartQuest("Q_LostAmulet")

    event OnObjectiveCompleted(quest: string, objective: string, index: int)
        print("objective done: " + objective)

    event OnQuestCompleted(quest: string, log: Actor)
        print("quest done: " + quest)
```
