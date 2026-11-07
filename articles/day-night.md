id: day-night
kind: recipe
title: Ciclo de dia e noite | A day and night cycle
keys: dia e noite, ciclo, sol se movendo, entardecer, anoitecer, horario do jogo, day night cycle, sun angle, time of day
--- pt
O sol gira com o tempo de jogo: um dia inteiro a cada `day_seconds` segundos.

```blueprint
Event Tick
  -> Set Sun Angle ( Pitch = Get Game Time in Seconds / Day Seconds * 360 - 90, Yaw = 30 )
```
```real
class DayNight extends Actor
    @editable
    var day_seconds = 120.0

    event Tick(dt: float)
        var angle = GetGameTimeInSeconds() / day_seconds * 360.0
        SetSunAngle(angle - 90.0, 30.0)
```

O céu, a luz e a exposição acompanham o sol sozinhos. Veja também [Céu e neblina](article:sky-fog).
--- en
The sun turns with the game time: a whole day every `day_seconds` seconds.

```blueprint
Event Tick
  -> Set Sun Angle ( Pitch = Get Game Time in Seconds / Day Seconds * 360 - 90, Yaw = 30 )
```
```real
class DayNight extends Actor
    @editable
    var day_seconds = 120.0

    event Tick(dt: float)
        var angle = GetGameTimeInSeconds() / day_seconds * 360.0
        SetSunAngle(angle - 90.0, 30.0)
```

The sky, the light and the exposure follow the sun by themselves. See also [Sky and fog](article:sky-fog).
