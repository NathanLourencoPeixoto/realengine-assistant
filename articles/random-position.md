id: random-position
kind: recipe
title: Posição aleatória | A random position
keys: aleatorio, posicao aleatoria, lugar aleatorio, sortear lugar, random, spawn aleatorio, random location, espalhar
--- pt
Ao começar, o ator pula para um ponto aleatório dentro de uma caixa em volta de onde estava.

```blueprint
Event BeginPlay
  -> Set Actor Location ( Random Point in Bounding Box( Get Actor Location, Area ) )
```
```real
class RandomSpot extends Actor
    @editable
    var area = Vector(1000, 1000, 0)

    event BeginPlay()
        SetActorLocation(RandomPointInBoundingBox(GetActorLocation(), area))
```

Outros sorteios: `RandomFloatInRange(a, b)`, `RandomIntegerInRange(a, b)`, `RandomBool()`; em Real também `random()` e `randint(a, b)`.
--- en
At the start, the actor jumps to a random point inside a box around where it was.

```blueprint
Event BeginPlay
  -> Set Actor Location ( Random Point in Bounding Box( Get Actor Location, Area ) )
```
```real
class RandomSpot extends Actor
    @editable
    var area = Vector(1000, 1000, 0)

    event BeginPlay()
        SetActorLocation(RandomPointInBoundingBox(GetActorLocation(), area))
```

Other draws: `RandomFloatInRange(a, b)`, `RandomIntegerInRange(a, b)`, `RandomBool()`; in Real also `random()` and `randint(a, b)`.
