id: gameplay-tags-list
kind: recipe
title: Lista de tags do projeto e achar atores por tag | The project's tag list and finding actors by tag
keys: lista de tags, tag list, gameplay tag list, project settings gameplay tags, renomear tag, rename tag, apagar tag, seletor de tag, tag picker, escolher tag, get all actors with tag, get all actors with gameplay tag, achar atores por tag, find actors by tag, todos os inimigos, all enemies, atores com tag, defaulgameplaytags, defaultgameplaytags.ini
--- pt
As tags ficam numa **lista do projeto**, como na Unreal: **Project Settings > Gameplay Tags** (arquivo `Config/DefaultGameplayTags.ini`).
- **Adicionar Gameplay Tag** (`Inimigo.Chefe`), **Adicionar Sub-tag** numa linha, **Renomear** (troca também as de baixo e as dos atores do nível) e **x** apaga da lista. **Trazer as Tags do Nível** junta as que os atores já usam.
- No **Details** e nos pinos dos nós de tag, a tag é escolhida num **seletor com busca e árvore**; digitar um nome novo o adiciona à lista.
- Para achar atores: **Get All Actors with Gameplay Tag** (a tag ou uma debaixo dela; **Exact Match** só o mesmo nome) e **Get All Actors with Tag** (exatamente aquele nome). Os dois leem só os atores que têm o componente Gameplay Tags. Chame uma vez (BeginPlay) e guarde o array.

```diagram steps
Project Settings > Gameplay Tags | Adicionar Inimigo, Inimigo.Chefe | Details > Gameplay Tags: escolher | Get All Actors with Gameplay Tag (Inimigo)
```
```blueprint
Event BeginPlay -> Get All Actors with Gameplay Tag ( Gameplay Tag = "Inimigo", Exact Match = false ) -> For Each Loop ( Out Actors ) -> Print String ( Get Display Name )
```
```real
class Contador extends Actor
    var total = 0

    event BeginPlay()
        var inimigos = GetAllActorsWithGameplayTag("Inimigo", false)
        for e in inimigos
            total += 1
        print("inimigos: {total}")
```
--- en
Tags live in a **project list**, like Unreal's: **Project Settings > Gameplay Tags** (the file `Config/DefaultGameplayTags.ini`).
- **Add New Gameplay Tag** (`Enemy.Boss`), **Add Sub-tag** on a row, **Rename** (also renames the ones under it and the level's actors') and **x** deletes from the list. **Add the Level's Tags** brings in the ones the actors already use.
- In the **Details** and on the tag nodes' pins, the tag is chosen in a **picker with a search and the tree**; typing a new name adds it to the list.
- To find actors: **Get All Actors with Gameplay Tag** (the tag or one under it; **Exact Match** only the same name) and **Get All Actors with Tag** (exactly that name). Both read only the actors with the Gameplay Tags component. Call it once (BeginPlay) and keep the array.

```diagram steps
Project Settings > Gameplay Tags | Add Enemy, Enemy.Boss | Details > Gameplay Tags: pick | Get All Actors with Gameplay Tag (Enemy)
```
```blueprint
Event BeginPlay -> Get All Actors with Gameplay Tag ( Gameplay Tag = "Enemy", Exact Match = false ) -> For Each Loop ( Out Actors ) -> Print String ( Get Display Name )
```
```real
class Counter extends Actor
    var total = 0

    event BeginPlay()
        var enemies = GetAllActorsWithGameplayTag("Enemy", false)
        for e in enemies
            total += 1
        print("enemies: {total}")
```
