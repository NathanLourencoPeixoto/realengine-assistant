id: look-at-player
kind: recipe
title: Virar para o jogador | Turn towards the player
keys: olhar para o jogador, virar para, encarar, mirar no jogador, torreta, look at player, face player, rotate towards, find look at rotation
--- pt
Uma torreta ou estátua que acompanha o jogador, girando suave.

```blueprint
Event Tick
  -> Want = Find Look at Rotation( Get Actor Location, Get Actor Location( Get Player Character ) )
  -> Set Actor Rotation ( RInterp To( Get Actor Rotation, Want, Delta Seconds, Turn Speed ) )
```
```real
class Watcher extends Actor
    @editable
    var turn_speed = 4.0

    event Tick(dt: float)
        var want = FindLookAtRotation(GetActorLocation(), GetPlayerCharacter().GetActorLocation())
        SetActorRotation(RInterpTo(GetActorRotation(), want, dt, turn_speed))
```
--- en
A turret or statue that follows the player, turning smoothly.

```blueprint
Event Tick
  -> Want = Find Look at Rotation( Get Actor Location, Get Actor Location( Get Player Character ) )
  -> Set Actor Rotation ( RInterp To( Get Actor Rotation, Want, Delta Seconds, Turn Speed ) )
```
```real
class Watcher extends Actor
    @editable
    var turn_speed = 4.0

    event Tick(dt: float)
        var want = FindLookAtRotation(GetActorLocation(), GetPlayerCharacter().GetActorLocation())
        SetActorRotation(RInterpTo(GetActorRotation(), want, dt, turn_speed))
```
