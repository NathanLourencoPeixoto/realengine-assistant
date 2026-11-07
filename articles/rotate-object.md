id: rotate-object
kind: recipe
title: Girar um objeto sem parar | Spin an object forever
keys: girar, rodar, rotacionar, girando, spin, rotate forever, ventilador, roda girando, helice, add actor local rotation
--- pt
Bom para moedas, ventiladores, rodas e itens que chamam atenção.

```blueprint
Event Tick (Delta Seconds)
  -> Add Actor Local Rotation
       Delta Rotation = Make Rotator( 0, Spin Speed * Delta Seconds, 0 )
```
```real
class Spinner extends Actor
    @editable
    var spin_speed = 90.0

    event Tick(dt: float)
        AddActorLocalRotation(Rotator(0, spin_speed * dt, 0))
```
```cs
public class SpinnerCs : Actor
{
    [Editable] float spinSpeed = 90.0f;

    void Tick(float dt)
    {
        AddActorLocalRotation(new Rotator(0, spinSpeed * dt, 0));
    }
}
```
```py
class SpinnerPy(Actor):
    spin_speed = 90.0

    def tick(self, dt: float):
        add_actor_local_rotation(Rotator(0, self.spin_speed * dt, 0))
```
--- en
Good for coins, fans, wheels and items that should catch the eye.

```blueprint
Event Tick (Delta Seconds)
  -> Add Actor Local Rotation
       Delta Rotation = Make Rotator( 0, Spin Speed * Delta Seconds, 0 )
```
```real
class Spinner extends Actor
    @editable
    var spin_speed = 90.0

    event Tick(dt: float)
        AddActorLocalRotation(Rotator(0, spin_speed * dt, 0))
```
```cs
public class SpinnerCs : Actor
{
    [Editable] float spinSpeed = 90.0f;

    void Tick(float dt)
    {
        AddActorLocalRotation(new Rotator(0, spinSpeed * dt, 0));
    }
}
```
```py
class SpinnerPy(Actor):
    spin_speed = 90.0

    def tick(self, dt: float):
        add_actor_local_rotation(Rotator(0, self.spin_speed * dt, 0))
```
