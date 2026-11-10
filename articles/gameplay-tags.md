id: gameplay-tags
kind: recipe
title: Gameplay Tags: marcar atores (Estado, Time, Dano) | Gameplay Tags: label actors (State, Team, Damage)
keys: gameplay tags, gameplay tag, tag, tags, etiqueta, marcar ator, actor has tag, has tag, time, equipe, team, estado, state, atordoado, stunned, imune, imunidade, tipo de dano, damage type, hierarquia, add gameplay tag, remove gameplay tag, has matching gameplay tag, matches tag
--- pt
Nomes com pontos que fazem uma hierarquia: `State.Stunned`, `Team.Red`, `Damage.Fire`. Um ator marcado `Damage.Fire` **tem** `Damage` (como o HasTag da Unreal).
- No nível: **Details > Adicionar > Gameplay Tags**, digite o nome e Enter (ou **+**); **x** tira.
- Em Blueprint (categoria **Gameplay Tags**): **Add Gameplay Tag**, **Remove Gameplay Tag**, **Has Matching Gameplay Tag** (a tag ou uma debaixo dela), **Has Gameplay Tag (Exact)** e **Matches Tag** (compara dois nomes).
- Sem Target ligado, vale o próprio ator. Até 16 tags por ator; o componente aparece sozinho na primeira Add.

```diagram steps
Inimigo leva choque | Add Gameplay Tag (State.Stunned) | Tick: Has Matching Gameplay Tag (State) ? | não anda | Delay 2 s -> Remove Gameplay Tag
```
```blueprint
Event BeginPlay -> Add Gameplay Tag ( Target = self, Tag = "Team.Red" )
Event Tick -> Branch ( Has Matching Gameplay Tag ( Target = self, Tag = "State" ) ) -> Print String ( "parado" )
```
```real
class Enemy extends Actor
    event BeginPlay()
        AddGameplayTag("Team.Red")

    event Stun()
        AddGameplayTag("State.Stunned")

    event Tick(dt: float)
        if HasMatchingGameplayTag("State")
            print("parado")
```
--- en
Names with dots that make a hierarchy: `State.Stunned`, `Team.Red`, `Damage.Fire`. An actor tagged `Damage.Fire` **has** `Damage` (like Unreal's HasTag).
- In the level: **Details > Add > Gameplay Tags**, type the name and Enter (or **+**); **x** removes.
- In a Blueprint (category **Gameplay Tags**): **Add Gameplay Tag**, **Remove Gameplay Tag**, **Has Matching Gameplay Tag** (the tag or one under it), **Has Gameplay Tag (Exact)** and **Matches Tag** (compares two names).
- With no Target wired, it is the actor itself. Up to 16 tags an actor; the component appears by itself on the first Add.

```diagram steps
Enemy gets shocked | Add Gameplay Tag (State.Stunned) | Tick: Has Matching Gameplay Tag (State) ? | doesn't walk | Delay 2 s -> Remove Gameplay Tag
```
```blueprint
Event BeginPlay -> Add Gameplay Tag ( Target = self, Tag = "Team.Red" )
Event Tick -> Branch ( Has Matching Gameplay Tag ( Target = self, Tag = "State" ) ) -> Print String ( "stopped" )
```
```real
class Enemy extends Actor
    event BeginPlay()
        AddGameplayTag("Team.Red")

    event Stun()
        AddGameplayTag("State.Stunned")

    event Tick(dt: float)
        if HasMatchingGameplayTag("State")
            print("stopped")
```
