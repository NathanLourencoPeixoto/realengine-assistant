id: moving-platform
kind: recipe
title: Plataforma que vai e volta | A platform that goes back and forth
keys: plataforma movel, plataforma que se mexe, elevador, vai e volta, moving platform, elevator, sobe e desce, oscilar, sin
--- pt
A plataforma oscila em torno de onde foi colocada (seno do tempo de jogo). Para um elevador, troque o eixo X pelo Z.

```blueprint
Event BeginPlay -> Set Start = Get Actor Location
Event Tick
  -> Set Actor Location
       New Location = Start + Make Vector( sin( Get Game Time in Seconds * Speed ) * Distance, 0, 0 )
```
```real
class MovingPlatform extends Actor
    @editable
    var distance = 300.0
    @editable
    var speed = 60.0
    var start = Vector(0, 0, 0)

    event BeginPlay()
        start = GetActorLocation()

    event Tick(dt: float)
        var offset = sin(GetGameTimeInSeconds() * speed) * distance
        SetActorLocation(start + Vector(offset, 0, 0))
```
```py
class MovingPlatformPy(Actor):
    distance = 300.0
    speed = 60.0
    start = Vector(0, 0, 0)

    def begin_play(self):
        self.start = get_actor_location()

    def tick(self, dt: float):
        offset = sin(get_game_time_in_seconds() * self.speed) * self.distance
        set_actor_location(self.start + Vector(offset, 0, 0))
```
--- en
The platform swings around where it was placed (the sine of the game time). For an elevator, swap the X axis for Z.

```blueprint
Event BeginPlay -> Set Start = Get Actor Location
Event Tick
  -> Set Actor Location
       New Location = Start + Make Vector( sin( Get Game Time in Seconds * Speed ) * Distance, 0, 0 )
```
```real
class MovingPlatform extends Actor
    @editable
    var distance = 300.0
    @editable
    var speed = 60.0
    var start = Vector(0, 0, 0)

    event BeginPlay()
        start = GetActorLocation()

    event Tick(dt: float)
        var offset = sin(GetGameTimeInSeconds() * speed) * distance
        SetActorLocation(start + Vector(offset, 0, 0))
```
```py
class MovingPlatformPy(Actor):
    distance = 300.0
    speed = 60.0
    start = Vector(0, 0, 0)

    def begin_play(self):
        self.start = get_actor_location()

    def tick(self, dt: float):
        offset = sin(get_game_time_in_seconds() * self.speed) * self.distance
        set_actor_location(self.start + Vector(offset, 0, 0))
```
