id: double-jump
kind: recipe
title: Pulo duplo | Double jump
keys: pular duas vezes, pulo duplo, double jump, pular no ar, salto duplo, jump twice, air jump, launch character, pulo extra
--- pt
O **Jump** só pula do chão; no ar, o segundo pulo usa **Launch Character** (joga o personagem para cima). Use num Character (o do jogador).

```blueprint
Event Tick
  -> Branch ( NOT Is Falling ) True -> Set Jumps = 0
  -> Branch ( Is Key Down [Space] AND NOT Was Down )
       True -> Branch ( NOT Is Falling )
                 True  -> Jump -> Set Jumps = 1
                 False -> Branch ( Jumps < 2 ) True -> Launch Character ( Make Vector(0, 0, Air Jump Speed), XY Override false, Z Override true ) -> Set Jumps = 2
  -> Set Was Down = Is Key Down [Space]
```
```real
class DoubleJumpHero extends Character
    @editable
    var air_jump_speed = 650.0
    var jumps = 0
    var was_down = false

    event Tick(dt: float)
        if not IsFalling()
            jumps = 0
        var down = IsKeyDown("Space")
        if down and not was_down
            if not IsFalling()
                Jump()
                jumps = 1
            elif jumps < 2
                LaunchCharacter(Vector(0, 0, air_jump_speed), false, true)
                jumps = 2
        was_down = down
```
```cs
public class DoubleJumpHeroCs : Character
{
    [Editable] float airJumpSpeed = 650.0f;
    int jumps = 0;
    bool wasDown = false;

    void Tick(float dt)
    {
        if (!IsFalling()) jumps = 0;
        bool down = IsKeyDown("Space");
        if (down && !wasDown)
        {
            if (!IsFalling()) { Jump(); jumps = 1; }
            else if (jumps < 2) { LaunchCharacter(new Vector(0, 0, airJumpSpeed), false, true); jumps = 2; }
        }
        wasDown = down;
    }
}
```
```py
class DoubleJumpHeroPy(Character):
    air_jump_speed = 650.0
    jumps = 0
    was_down = False

    def tick(self, dt: float):
        if not is_falling():
            self.jumps = 0
        down = is_key_down("Space")
        if down and not self.was_down:
            if not is_falling():
                jump()
                self.jumps = 1
            elif self.jumps < 2:
                launch_character(Vector(0, 0, self.air_jump_speed), False, True)
                self.jumps = 2
        self.was_down = down
```

`air_jump_speed` aparece no Details: suba para pular mais alto.
--- en
**Jump** only jumps from the ground; in the air, the second jump uses **Launch Character** (throws the character up). Use it on a Character (the player's).

```blueprint
Event Tick
  -> Branch ( NOT Is Falling ) True -> Set Jumps = 0
  -> Branch ( Is Key Down [Space] AND NOT Was Down )
       True -> Branch ( NOT Is Falling )
                 True  -> Jump -> Set Jumps = 1
                 False -> Branch ( Jumps < 2 ) True -> Launch Character ( Make Vector(0, 0, Air Jump Speed), XY Override false, Z Override true ) -> Set Jumps = 2
  -> Set Was Down = Is Key Down [Space]
```
```real
class DoubleJumpHero extends Character
    @editable
    var air_jump_speed = 650.0
    var jumps = 0
    var was_down = false

    event Tick(dt: float)
        if not IsFalling()
            jumps = 0
        var down = IsKeyDown("Space")
        if down and not was_down
            if not IsFalling()
                Jump()
                jumps = 1
            elif jumps < 2
                LaunchCharacter(Vector(0, 0, air_jump_speed), false, true)
                jumps = 2
        was_down = down
```
```cs
public class DoubleJumpHeroCs : Character
{
    [Editable] float airJumpSpeed = 650.0f;
    int jumps = 0;
    bool wasDown = false;

    void Tick(float dt)
    {
        if (!IsFalling()) jumps = 0;
        bool down = IsKeyDown("Space");
        if (down && !wasDown)
        {
            if (!IsFalling()) { Jump(); jumps = 1; }
            else if (jumps < 2) { LaunchCharacter(new Vector(0, 0, airJumpSpeed), false, true); jumps = 2; }
        }
        wasDown = down;
    }
}
```
```py
class DoubleJumpHeroPy(Character):
    air_jump_speed = 650.0
    jumps = 0
    was_down = False

    def tick(self, dt: float):
        if not is_falling():
            self.jumps = 0
        down = is_key_down("Space")
        if down and not self.was_down:
            if not is_falling():
                jump()
                self.jumps = 1
            elif self.jumps < 2:
                launch_character(Vector(0, 0, self.air_jump_speed), False, True)
                self.jumps = 2
        self.was_down = down
```

`air_jump_speed` shows in Details: raise it to jump higher.
