id: fog-change
kind: recipe
title: Mudar a neblina pelo jogo | Change the fog during the game
keys: neblina, nevoa, fog, cerracao, clima mudando, fog density, ficar nublado
--- pt
Uma zona que deixa a neblina densa quando o jogador entra (precisa de uma Exponential Height Fog no nível).

```blueprint
Event ActorBeginOverlap -> Set Fog Density ( 0.05 )
Event ActorEndOverlap -> Set Fog Density ( 0.002 )
```
```real
class FogZone extends Actor
    event OnBeginOverlap(other: Actor)
        SetFogDensity(0.05)

    event OnEndOverlap(other: Actor)
        SetFogDensity(0.002)
```
--- en
A zone that makes the fog thick when the player walks in (the level needs an Exponential Height Fog).

```blueprint
Event ActorBeginOverlap -> Set Fog Density ( 0.05 )
Event ActorEndOverlap -> Set Fog Density ( 0.002 )
```
```real
class FogZone extends Actor
    event OnBeginOverlap(other: Actor)
        SetFogDensity(0.05)

    event OnEndOverlap(other: Actor)
        SetFogDensity(0.002)
```
