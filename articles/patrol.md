id: patrol
kind: recipe
title: NPC que patrulha entre dois pontos | An NPC patrolling between two points
keys: patrulha, patrulhar, ronda, ir e voltar, waypoint, npc andando, guarda, patrol, ai move to
--- pt
O personagem anda até A, depois até B, e repete (com **AI Move To**, que acha o caminho).

```blueprint
Event Tick
  -> Target = Select( Going B, Point B, Point A )
  -> AI Move To ( Pawn = self, Destination = Target, Acceptance Radius = 50 )
  -> Branch ( Distance( Get Actor Location, Target ) < 100 ) True -> Set Going B = NOT Going B
```
```real
class Patroller extends Character
    @editable
    var point_a = Vector(0, 0, 0)
    @editable
    var point_b = Vector(1000, 0, 0)
    var going_b = true

    event Tick(dt: float)
        var target = point_a
        if going_b
            target = point_b
        AIMoveTo(self, target, 50.0)
        if GetActorLocation().Distance(target) < 100.0
            going_b = not going_b
```

Para mais pontos, guarde um array de vetores. Para patrulhar, ver o jogador e perseguir, use uma Behavior Tree.
--- en
The character walks to A, then to B, and repeats (with **AI Move To**, which finds the path).

```blueprint
Event Tick
  -> Target = Select( Going B, Point B, Point A )
  -> AI Move To ( Pawn = self, Destination = Target, Acceptance Radius = 50 )
  -> Branch ( Distance( Get Actor Location, Target ) < 100 ) True -> Set Going B = NOT Going B
```
```real
class Patroller extends Character
    @editable
    var point_a = Vector(0, 0, 0)
    @editable
    var point_b = Vector(1000, 0, 0)
    var going_b = true

    event Tick(dt: float)
        var target = point_a
        if going_b
            target = point_b
        AIMoveTo(self, target, 50.0)
        if GetActorLocation().Distance(target) < 100.0
            going_b = not going_b
```

For more points, keep an array of vectors. To patrol, spot the player and chase, use a Behavior Tree.
