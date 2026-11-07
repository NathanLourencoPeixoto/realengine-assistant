id: physics-push
kind: recipe
title: Empurrar com física | Push with physics
keys: empurrar, impulso, explosao, chutar objeto, jogar longe, push, impulse, launch object, add impulse
--- pt
O ator precisa de **Simulate Physics** ligado. O impulso é aplicado uma vez.

```blueprint
Event BeginPlay
  -> Set Simulate Physics ( Target = self, Simulate = true )
  -> Add Impulse ( Target = self, Impulse = Make Vector( 0, 0, 800 ), Vel Change = true )
```
```real
class Popper extends Actor
    event BeginPlay()
        SetSimulatePhysics(true)
        AddImpulse(Vector(0, 0, 800), true)
```

Uma explosão que empurra tudo em volta: `AddRadialImpulse(centro, raio, força)`.
--- en
The actor needs **Simulate Physics** on. The impulse is applied once.

```blueprint
Event BeginPlay
  -> Set Simulate Physics ( Target = self, Simulate = true )
  -> Add Impulse ( Target = self, Impulse = Make Vector( 0, 0, 800 ), Vel Change = true )
```
```real
class Popper extends Actor
    event BeginPlay()
        SetSimulatePhysics(true)
        AddImpulse(Vector(0, 0, 800), true)
```

An explosion pushing everything around: `AddRadialImpulse(center, radius, strength)`.
