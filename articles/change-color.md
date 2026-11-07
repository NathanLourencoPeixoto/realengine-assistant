id: change-color
kind: recipe
title: Mudar a cor de um objeto | Change an object's color
keys: mudar cor, trocar cor, pintar objeto, colorir, vermelho, change color, set color, piscar cor, set base color
--- pt
Muda a cor base do material do ator (sem mexer no asset do material). Para cores por parâmetro, use uma Material Instance.

```blueprint
Event BeginPlay
  -> Set Base Color
       Target = self, Color = Make Vector( 1, 0, 0 )   (vermelho)
```
```real
class RedThing extends Actor
    event BeginPlay()
        SetBaseColor(Vector(1, 0, 0))
```
```cs
public class RedThingCs : Actor
{
    void BeginPlay()
    {
        SetBaseColor(new Vector(1, 0, 0));
    }
}
```
--- en
Changes the base color of the actor's material (the material asset untouched). For colors by parameter, use a Material Instance.

```blueprint
Event BeginPlay
  -> Set Base Color
       Target = self, Color = Make Vector( 1, 0, 0 )   (red)
```
```real
class RedThing extends Actor
    event BeginPlay()
        SetBaseColor(Vector(1, 0, 0))
```
```cs
public class RedThingCs : Actor
{
    void BeginPlay()
    {
        SetBaseColor(new Vector(1, 0, 0));
    }
}
```
