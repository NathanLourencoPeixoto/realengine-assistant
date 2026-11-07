id: teleport
kind: recipe
title: Teleporte | Teleport
keys: teleporte, teleportar, portal, mandar o jogador para outro lugar, teleport, warp, set actor location
--- pt
Quem encosta vai para o destino (um ponto editável no Details).

```blueprint
Event ActorBeginOverlap (Other Actor)
  -> Set Actor Location ( Target = Other Actor, New Location = Destination )
```
```real
class Teleporter extends Actor
    @editable
    var destination = Vector(0, 0, 300)

    event OnBeginOverlap(other: Actor)
        other.SetActorLocation(destination)
```
--- en
Whoever touches it goes to the destination (a point editable in Details).

```blueprint
Event ActorBeginOverlap (Other Actor)
  -> Set Actor Location ( Target = Other Actor, New Location = Destination )
```
```real
class Teleporter extends Actor
    @editable
    var destination = Vector(0, 0, 300)

    event OnBeginOverlap(other: Actor)
        other.SetActorLocation(destination)
```
