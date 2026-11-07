id: door-open
kind: recipe
title: Porta que abre sozinha | A door that opens by itself
keys: porta, abrir porta, door, open door, porta automatica, chegar perto, distancia do jogador, girar porta
--- pt
A porta gira suavemente quando o jogador chega perto e fecha quando ele se afasta. Ponha o pivô da malha na dobradiça.

```blueprint
Event Tick
  -> Target = Select Float( Get Distance To( Get Player Character ) < Open Distance, Open Angle, 0 )
  -> Set Angle = FInterp To( Angle, Target, Delta Seconds, 4 )
  -> Set Actor Rotation ( Make Rotator( 0, Angle, 0 ) )
```
```real
class AutoDoor extends Actor
    @editable
    var open_distance = 300.0
    @editable
    var open_angle = 90.0
    var angle = 0.0

    event Tick(dt: float)
        var target = 0.0
        if GetDistanceTo(GetPlayerCharacter()) < open_distance
            target = open_angle
        angle = angle + (target - angle) * clamp(dt * 4.0, 0.0, 1.0)
        SetActorRotation(Rotator(0, angle, 0))
```
```cs
public class AutoDoorCs : Actor
{
    [Editable] float openDistance = 300.0f;
    [Editable] float openAngle = 90.0f;
    float angle = 0.0f;

    void Tick(float dt)
    {
        float target = 0.0f;
        if (GetDistanceTo(GetPlayerCharacter()) < openDistance) target = openAngle;
        angle = angle + (target - angle) * clamp(dt * 4.0f, 0.0f, 1.0f);
        SetActorRotation(new Rotator(0, angle, 0));
    }
}
```
--- en
The door swings smoothly when the player comes near and closes when they leave. Put the mesh's pivot at the hinge.

```blueprint
Event Tick
  -> Target = Select Float( Get Distance To( Get Player Character ) < Open Distance, Open Angle, 0 )
  -> Set Angle = FInterp To( Angle, Target, Delta Seconds, 4 )
  -> Set Actor Rotation ( Make Rotator( 0, Angle, 0 ) )
```
```real
class AutoDoor extends Actor
    @editable
    var open_distance = 300.0
    @editable
    var open_angle = 90.0
    var angle = 0.0

    event Tick(dt: float)
        var target = 0.0
        if GetDistanceTo(GetPlayerCharacter()) < open_distance
            target = open_angle
        angle = angle + (target - angle) * clamp(dt * 4.0, 0.0, 1.0)
        SetActorRotation(Rotator(0, angle, 0))
```
```cs
public class AutoDoorCs : Actor
{
    [Editable] float openDistance = 300.0f;
    [Editable] float openAngle = 90.0f;
    float angle = 0.0f;

    void Tick(float dt)
    {
        float target = 0.0f;
        if (GetDistanceTo(GetPlayerCharacter()) < openDistance) target = openAngle;
        angle = angle + (target - angle) * clamp(dt * 4.0f, 0.0f, 1.0f);
        SetActorRotation(new Rotator(0, angle, 0));
    }
}
```
