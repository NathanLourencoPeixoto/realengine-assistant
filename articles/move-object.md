id: move-object
kind: recipe
title: Fazer um objeto andar sozinho | Make an object move by itself
keys: mover objeto, andar sozinho, se mexer, deslizar, movimento, move object, translate, carrinho andando, objeto se movendo, add actor world offset
--- pt
A cada quadro o objeto anda um pouco. Multiplicar pela duração do quadro (`dt`) deixa a velocidade igual em qualquer PC.

```blueprint
Event Tick (Delta Seconds)
  -> Add Actor World Offset
       Delta Location = Make Vector( Speed * Delta Seconds, 0, 0 )
(Speed: uma variável Float, Instance Editable)
```
```real
class Mover extends Actor
    @editable
    var speed = 200.0

    event Tick(dt: float)
        AddActorWorldOffset(Vector(speed * dt, 0, 0))
```
```cs
public class MoverCs : Actor
{
    [Editable] float speed = 200.0f;

    void Tick(float dt)
    {
        AddActorWorldOffset(new Vector(speed * dt, 0, 0));
    }
}
```
```py
class MoverPy(Actor):
    speed = 200.0

    def tick(self, dt: float):
        add_actor_world_offset(Vector(self.speed * dt, 0, 0))
```
```c
// parent: Actor
float speed = 200.0f;

void Tick(float dt)
{
    AddActorWorldOffset(Vector(speed * dt, 0, 0));
}
```
--- en
Each frame the object moves a bit. Multiplying by the frame's duration (`dt`) keeps the speed the same on any PC.

```blueprint
Event Tick (Delta Seconds)
  -> Add Actor World Offset
       Delta Location = Make Vector( Speed * Delta Seconds, 0, 0 )
(Speed: a Float variable, Instance Editable)
```
```real
class Mover extends Actor
    @editable
    var speed = 200.0

    event Tick(dt: float)
        AddActorWorldOffset(Vector(speed * dt, 0, 0))
```
```cs
public class MoverCs : Actor
{
    [Editable] float speed = 200.0f;

    void Tick(float dt)
    {
        AddActorWorldOffset(new Vector(speed * dt, 0, 0));
    }
}
```
```py
class MoverPy(Actor):
    speed = 200.0

    def tick(self, dt: float):
        add_actor_world_offset(Vector(self.speed * dt, 0, 0))
```
```c
// parent: Actor
float speed = 200.0f;

void Tick(float dt)
{
    AddActorWorldOffset(Vector(speed * dt, 0, 0));
}
```
