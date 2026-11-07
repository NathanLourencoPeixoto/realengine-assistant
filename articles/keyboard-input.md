id: keyboard-input
kind: recipe
title: Ler o teclado | Read the keyboard
keys: teclado, apertar tecla, tecla pressionada, input, controle, setas, wasd, keyboard, key press, is key down, quando apertar
--- pt
Pergunte a cada quadro se a tecla está apertada. Os nomes: letras ("E"), números, "Space", "LeftShift", "Up", "Down", "Left", "Right", "F1"...

```blueprint
Event Tick
  -> Branch ( Is Key Down [Up] )
       True -> Add Actor World Offset ( Make Vector( Speed * Delta Seconds, 0, 0 ) )
(Is Key Down: a tecla escolhida no Details do nó)
```
```real
class KeyMover extends Actor
    @editable
    var speed = 300.0

    event Tick(dt: float)
        if IsKeyDown("Up")
            AddActorWorldOffset(Vector(speed * dt, 0, 0))
        if IsKeyDown("Down")
            AddActorWorldOffset(Vector(-speed * dt, 0, 0))
```
```cs
public class KeyMoverCs : Actor
{
    [Editable] float speed = 300.0f;

    void Tick(float dt)
    {
        if (IsKeyDown("Up")) AddActorWorldOffset(new Vector(speed * dt, 0, 0));
        if (IsKeyDown("Down")) AddActorWorldOffset(new Vector(-speed * dt, 0, 0));
    }
}
```
```py
class KeyMoverPy(Actor):
    speed = 300.0

    def tick(self, dt: float):
        if is_key_down("Up"):
            add_actor_world_offset(Vector(self.speed * dt, 0, 0))
        if is_key_down("Down"):
            add_actor_world_offset(Vector(-self.speed * dt, 0, 0))
```

Para o personagem, os modelos já usam as ações de entrada (Configurações do Projeto > Input); este jeito serve para qualquer ator.
--- en
Ask each frame whether the key is held. The names: letters ("E"), digits, "Space", "LeftShift", "Up", "Down", "Left", "Right", "F1"...

```blueprint
Event Tick
  -> Branch ( Is Key Down [Up] )
       True -> Add Actor World Offset ( Make Vector( Speed * Delta Seconds, 0, 0 ) )
(Is Key Down: the key picked in the node's Details)
```
```real
class KeyMover extends Actor
    @editable
    var speed = 300.0

    event Tick(dt: float)
        if IsKeyDown("Up")
            AddActorWorldOffset(Vector(speed * dt, 0, 0))
        if IsKeyDown("Down")
            AddActorWorldOffset(Vector(-speed * dt, 0, 0))
```
```cs
public class KeyMoverCs : Actor
{
    [Editable] float speed = 300.0f;

    void Tick(float dt)
    {
        if (IsKeyDown("Up")) AddActorWorldOffset(new Vector(speed * dt, 0, 0));
        if (IsKeyDown("Down")) AddActorWorldOffset(new Vector(-speed * dt, 0, 0));
    }
}
```
```py
class KeyMoverPy(Actor):
    speed = 300.0

    def tick(self, dt: float):
        if is_key_down("Up"):
            add_actor_world_offset(Vector(self.speed * dt, 0, 0))
        if is_key_down("Down"):
            add_actor_world_offset(Vector(-self.speed * dt, 0, 0))
```

For the character, the templates already use input actions (Project Settings > Input); this way works for any actor.
