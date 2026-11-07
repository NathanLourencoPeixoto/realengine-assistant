id: procedural-worlds
kind: recipe
title: Mundos procedurais: terreno infinito, biomas, criaturas | Procedural worlds: endless terrain, biomes, creatures
keys: procedural, procedural world, mundo procedural, geracao procedural, procedural generation, mapa procedural, procedural map, minecraft, peak, mundo infinito, endless world, infinite world, terreno, terrain, bioma, biome, semente, seed, chunk, streaming, longas distancias, long distances, 100 km, origin rebasing, rebase, spawn de criaturas, creature spawn, estruturas, structures, ruinas, ruins, arvores, trees, open world, mundo aberto
--- pt
```diagram steps
Adicionar Rápido > Procedural > Mundo Procedural > Terreno | Detalhes: semente, blocos, altura, água, biomas, árvores, estruturas, criaturas | Play: o mundo cresce em volta do jogador | Classe da Criatura e Classe da Estrutura: seus Blueprints
```
## Como funciona
O **Mundo Procedural** faz o terreno em volta do jogador a partir de uma **semente**. A mesma semente dá sempre o mesmo mundo, como no Minecraft.

**O terreno**
- Colunas de blocos em **chunks** carregados conforme o jogador anda: finos perto e grossos longe (anéis de detalhe até a Distância de Visão).
- O *Degrau de Altura* define o estilo: 100 cm dá blocos como no Minecraft; 25 cm dá terraços suaves.
- **Biomas**: planície, floresta, deserto, neve, montanhas com pico nevado, praias, lagos e mar (um Corpo d'Água onde barcos flutuam).
- **Árvores**, **ruínas** e **torres** espalhadas pelo terreno.
- **Criaturas** nascem perto do jogador conforme a densidade. Por padrão é o Mannequin com o BT_Chase; ponha a sua classe em *Classe da Criatura* (e a sua estrutura em *Classe da Estrutura*).
- Personagens, IA, veículos e ragdolls pisam no mesmo chão.

**Longas distâncias**
- Os chunks têm coordenadas inteiras e o ruído é de precisão dupla, então o mundo continua igual a 100 km ou a 10.000 km.
- Quando o jogador passa da *Distância do Rebase*, o mundo inteiro volta para perto do 0 (o World Origin Rebasing da Unreal), e as posições mantêm a precisão de centímetro.
- No jogo, isso custa cerca de 1,5 ms por quadro enquanto se viaja a 250 m/s.

```blueprint
Event BeginPlay -> Set Actor Location ( Target, Location )
```
```real
class Explorer extends Actor
    event BeginPlay()
        SetActorLocation(Vector(0, 0, 3000))
```
Veja também [Instalações procedurais](article:procedural-facility).
--- en
```diagram steps
Quick Add > Procedural > Procedural World > Terrain | Details: seed, blocks, height, water, biomes, trees, structures, creatures | Play: the world grows around the player | Creature Class and Structure Class: your Blueprints
```
## How it works
The **Procedural World** makes the terrain around the player from a **seed**. The same seed always gives the same world, as in Minecraft.

**The terrain**
- Columns of blocks in **chunks** that stream in as the player moves: fine near and coarse far (rings of detail out to the View Distance).
- *Height Step* sets the style: 100 cm gives Minecraft-like blocks; 25 cm gives gentle terraces.
- **Biomes**: plains, forest, desert, snow, mountains with snowy peaks, beaches, lakes and sea (a Water Body boats float on).
- **Trees**, **ruins** and **towers** scattered over the land.
- **Creatures** spawn near the player by their density. The default is the Mannequin with BT_Chase; put your own class in *Creature Class* (and your structure in *Structure Class*).
- Characters, AI, vehicles and ragdolls stand on the same ground.

**Long distances**
- The chunks have integer coordinates and the noise is double precision, so the world stays the same at 100 km or 10,000 km.
- Past the *Rebase Distance*, the whole world moves back near 0 (Unreal's World Origin Rebasing), so positions keep centimeter precision.
- In game, this costs about 1.5 ms a frame while traveling at 250 m/s.

```blueprint
Event BeginPlay -> Set Actor Location ( Target, Location )
```
```real
class Explorer extends Actor
    event BeginPlay()
        SetActorLocation(Vector(0, 0, 3000))
```
See also [Procedural facilities](article:procedural-facility).
