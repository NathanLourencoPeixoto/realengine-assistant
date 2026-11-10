id: world-partition
kind: concept
title: Mundos grandes (World Partition, Data Layers, HLOD) | Big worlds (World Partition, Data Layers, HLOD)
keys: world partition, mundo aberto grande, carregando por distancia, carregar por distancia, carregar o mapa por partes, mapa por partes, camadas de atores, ligar e desligar camadas, ligar camada, desligar camada, mostrar e esconder grupos de atores no jogo, actor layers, toggle layers at runtime, mundo grande, mundos grandes, mundo aberto, open world, big world, large world, big level, nivel grande, mapa grande, streaming, level streaming, streaming de nivel, carregar por distancia, load by distance, grade, grid, cell, celula, celulas, loading range, alcance de carga, data layer, data layers, camada de dados, camadas, hlod, lod de longe, far lod, distant meshes, malhas distantes, merged mesh, malha combinada, build hlods, construir hlods, is spatially loaded, carregado espacialmente, set data layer runtime state, is location loaded, engasgo, travada, hitch, stutter, 4 km, mil atores, thousands of actors
--- pt
```diagram steps
Adicionar > Landscape > World Partition (um por nível)
Os atores entram na grade de células (128 m) sozinhos
Compilar > Construir HLODs: o que está longe vira uma malha só
Play: as células perto da câmera entram, as de longe saem, sem engasgo
```
O **World Partition** deixa um nível enorme rodar como um pequeno: só o que está perto do jogador fica no mundo (como o da Unreal).
- **Como ligar:** **Adicionar > Landscape > World Partition**. Nos Details dele: **Cell Size** (128 m), **Loading Range** (256 m: as células até essa distância da câmera ficam no mundo) e **Streaming Budget** (ms por quadro para carregar e descarregar: o resto espera o próximo quadro, os mais perto primeiro).
- **Quem entra na grade:** cada ator tem **World Partition > Is Spatially Loaded**. **Auto** põe na grade os props, luzes locais, pickups, inimigos e Blueprints; o sol, o céu, a neblina, o Landscape, o jogador, as regras do jogo e os volumes grandes ficam sempre. **No** prende um ator no mundo (o chão de uma peça só, por exemplo).
- **Ao voltar:** um ator que saiu volta como o nível o tinha (o reset da Unreal). Para guardar o que mudou (um baú aberto, um inimigo morto), use o componente **Salvável**.
- **Data Layers:** nos Details do World Partition, **+ Data Layer** cria uma camada com nome e **estado inicial**: **Unloaded** (fora), **Loaded** (dentro, escondida) ou **Activated** (dentro e visível). Marque a camada nos Details de cada ator. No jogo, **Set Data Layer Runtime State** troca o estado: o interior de uma masmorra, a cidade antes e depois da batalha, a decoração de um evento. O olho ao lado do nome esconde a camada no editor.
- **HLOD (o que se vê de longe):** perto do limite, os atores que saíram continuam visíveis como **proxies** (a mesma malha, sem Blueprint, sem colisão). Longe, **Compilar > Construir HLODs** junta cada região de 4 x 4 células numa malha só, simplificada (**HLOD Triangles**, 5 %) e com os materiais assados nas cores dos vértices (`Content/HLOD/<nível>/`). Malhas menores que **HLOD Min Size** ficam de fora.
- **Is Location Loaded:** verdadeiro quando a célula de um ponto está no mundo: espere por ele antes de teleportar ou criar algo lá.
- **O mapa:** os Details do World Partition mostram as células (mais claras: mais atores) e o círculo do Loading Range; no Play, as verdes estão no mundo e as azuis aparecem pelo HLOD.
- **Custo** (RTX 3060, cena `wp`: 4 x 4 km, 6000 atores, atravessada a 400 m/s): 252 fps contra 240 fps com tudo carregado, 0,05 ms por quadro de streaming (pior 0,26 ms) e 0,16 % de quadros acima do dobro da mediana, contra 3,2 % sem ele.
- **Cuidado:** um ator da grade não deve guardar referência a outro de outra célula (ele pode não estar lá), como na Unreal.
```blueprint
Event BeginPlay -> Set Data Layer Runtime State ( Data Layer = "Dungeon", State = 2 )
Event Key E -> Branch ( Is Location Loaded ( Location = Target ) ) -> Set Actor Location ( New Location = Target )
```
```real
class Portao extends Actor
    var Destino: Vector

    event BeginPlay()
        SetDataLayerRuntimeState("Masmorra", 2)

    event Tick(dt: float)
        if IsLocationLoaded(Destino)
            print("o destino ja esta no mundo")
```
--- en
```diagram steps
Add > Landscape > World Partition (one per level)
The actors join the grid of cells (128 m) by themselves
Build > Build HLODs: what is far becomes a single mesh
Play: the cells near the camera come in, the far ones leave, no hitch
```
**World Partition** lets a huge level run like a small one: only what is near the player stays in the world (like Unreal's).
- **How to turn it on:** **Add > Landscape > World Partition**. In its Details: **Cell Size** (128 m), **Loading Range** (256 m: the cells this close to the camera stay in the world) and **Streaming Budget** (ms a frame for loading and unloading: the rest waits for the next frame, the nearest first).
- **Who joins the grid:** each actor has **World Partition > Is Spatially Loaded**. **Auto** puts props, local lights, pickups, enemies and Blueprints on the grid; the sun, the sky, the fog, the Landscape, the player, the game's rules and big volumes always stay. **No** keeps an actor in the world (a one-piece floor, for instance).
- **When it comes back:** an actor that left returns as the level had it (Unreal's reset). To keep what changed (an opened chest, a dead enemy), use the **Saveable** component.
- **Data Layers:** in the World Partition's Details, **+ Data Layer** makes a named layer with an **initial state**: **Unloaded** (out), **Loaded** (in, hidden) or **Activated** (in and shown). Tick the layer in each actor's Details. In the game, **Set Data Layer Runtime State** changes it: a dungeon's interior, the town before and after the battle, an event's decorations. The eye next to the name hides the layer in the editor.
- **HLOD (what you see from far):** near the edge, the actors that left stay visible as **proxies** (the same mesh, no Blueprint, no collision). Far away, **Build > Build HLODs** merges each region of 4 x 4 cells into one mesh, simplified (**HLOD Triangles**, 5 %) with the materials baked into vertex colors (`Content/HLOD/<level>/`). Meshes smaller than **HLOD Min Size** are left out.
- **Is Location Loaded:** true when a point's cell is in the world: wait for it before teleporting or spawning something there.
- **The map:** the World Partition's Details show the cells (lighter: more actors) and the Loading Range's circle; in Play, the green ones are in the world and the blue ones show through their HLOD.
- **Cost** (RTX 3060, scene `wp`: 4 x 4 km, 6000 actors, crossed at 400 m/s): 252 fps against 240 fps with everything loaded, 0.05 ms a frame of streaming (worst 0.26 ms) and 0.16 % of frames over twice the median, against 3.2 % without it.
- **Careful:** an actor on the grid shouldn't keep a reference to one in another cell (it may not be there), as in Unreal.
```blueprint
Event BeginPlay -> Set Data Layer Runtime State ( Data Layer = "Dungeon", State = 2 )
Event Key E -> Branch ( Is Location Loaded ( Location = Target ) ) -> Set Actor Location ( New Location = Target )
```
```real
class Gate extends Actor
    var Destination: Vector

    event BeginPlay()
        SetDataLayerRuntimeState("Dungeon", 2)

    event Tick(dt: float)
        if IsLocationLoaded(Destination)
            print("the destination is in the world")
```
