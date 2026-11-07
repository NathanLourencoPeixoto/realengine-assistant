id: procedural-facility
kind: recipe
title: Instalações procedurais: salas, corredores, monstros | Procedural facilities: rooms, corridors, monsters
keys: instalacao procedural, procedural facility, dungeon, masmorra, lethal company, repo, salas, rooms, corredores, corridors, portas, doors, labirinto, maze, gerar mapa, generate map, roguelike, terror, horror, scrap, itens, items, monstros, monsters
--- pt
```diagram steps
Adicionar Rápido > Procedural > Mundo Procedural > Instalação | Detalhes: semente, salas, tamanho, altura, laços | A entrada é o lugar do ator | Play: monstros nas salas mais fundas
```
## Como funciona
No modo **Instalação**, o Mundo Procedural cresce salas a partir da **entrada** (o lugar do ator), como em Lethal Company e Repo:

**A planta**
- Cada sala nova sai de uma sala que já existe por uma **porta**. Isso garante que toda sala pode ser alcançada.
- *Laços* abre portas extras entre vizinhas, para dar caminhos alternativos.
- As salas são blocos de prototipagem: personagens e IA andam e colidem com elas na hora.

**O que vai em cada sala**
- **Luz**: uma por sala, mais quente quanto mais funda a sala.
- **Itens**: caixas douradas para achar (troque por um Blueprint com *Spawn Actor*).
- **Monstros**: mais comuns nas salas mais fundas. Use a sua classe em *Classe da Criatura*.

A mesma semente dá a mesma instalação; mude a semente e cada partida tem outra planta.

```blueprint
Event BeginPlay -> Spawn Actor from Class ( Class, Spawn Transform )
```
```real
class Run extends Actor
    event BeginPlay()
        SetActorLocation(Vector(0, -200, 100))
```
Veja também [Mundos procedurais](article:procedural-worlds).
--- en
```diagram steps
Quick Add > Procedural > Procedural World > Facility | Details: seed, rooms, size, height, loops | The entrance is the actor's place | Play: monsters in the deeper rooms
```
## How it works
In **Facility** mode the Procedural World grows rooms from the **entrance** (the actor's place), as in Lethal Company and Repo:

**The layout**
- Every new room grows out of an existing one through a **door**. That guarantees every room can be reached.
- *Loops* opens extra doors between neighbors, for alternative paths.
- The rooms are prototyping blocks: Characters and the AI walk on and collide with them at once.

**What goes in each room**
- **Light**: one per room, warmer the deeper the room.
- **Items**: golden boxes to find (swap them for a Blueprint with *Spawn Actor*).
- **Monsters**: more common in the deeper rooms. Use your own class in *Creature Class*.

The same seed gives the same facility; change the seed and each run gets a new layout.

```blueprint
Event BeginPlay -> Spawn Actor from Class ( Class, Spawn Transform )
```
```real
class Run extends Actor
    event BeginPlay()
        SetActorLocation(Vector(0, -200, 100))
```
See also [Procedural worlds](article:procedural-worlds).
