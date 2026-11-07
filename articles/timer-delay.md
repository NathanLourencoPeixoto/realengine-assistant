id: timer-delay
kind: recipe
title: Esperar alguns segundos | Wait a few seconds
keys: esperar, aguardar, delay, depois de segundos, temporizador, timer, contagem regressiva, bomba relogio, wait seconds, cooldown
--- pt
**Delay** pausa só aquele evento: o resto do jogo continua.

```blueprint
Event BeginPlay
  -> Print String ( "3..." )
  -> Delay ( Duration = 3.0 )
  -> Print String ( "Bum!" )
  -> Destroy Actor
```
```real
class Bomb extends Actor
    @editable
    var fuse = 3.0

    event BeginPlay()
        print("Tick tock...")
        Delay(fuse)
        print("Boom!")
        DestroyActor()
```

Para repetir de tempos em tempos, use **Set Timer by Event** com Looping ligado.
--- en
**Delay** pauses only that event: the rest of the game goes on.

```blueprint
Event BeginPlay
  -> Print String ( "3..." )
  -> Delay ( Duration = 3.0 )
  -> Print String ( "Boom!" )
  -> Destroy Actor
```
```real
class Bomb extends Actor
    @editable
    var fuse = 3.0

    event BeginPlay()
        print("Tick tock...")
        Delay(fuse)
        print("Boom!")
        DestroyActor()
```

To repeat every so often, use **Set Timer by Event** with Looping on.
