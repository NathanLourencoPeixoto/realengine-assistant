id: health-damage
kind: recipe
title: Vida e dano | Health and damage
keys: vida, hp, dano, machucar, morrer, health, damage, take damage, levar dano, perder vida, barra de vida, matar inimigo
--- pt
Uma variável de vida, uma função que tira vida e o ator some quando chega a zero. Aqui o dano vem de qualquer coisa que encosta.

```blueprint
Event BeginPlay -> Set HP = Max HP
Event ActorBeginOverlap -> Take Hit ( Amount = 25 )
Função Take Hit (Amount)
  -> Set HP = Clamp( HP - Amount, 0, Max HP )
  -> Branch ( HP <= 0 ) True -> Destroy Actor
```
```real
class Damageable extends Actor
    @editable
    var max_hp = 100.0
    var hp = 0.0

    event BeginPlay()
        hp = max_hp

    event OnBeginOverlap(other: Actor)
        TakeHit(25.0)

    func TakeHit(amount: float)
        hp = clamp(hp - amount, 0.0, max_hp)
        print("HP: {hp}")
        if hp <= 0.0
            DestroyActor()
```
```cs
public class DamageableCs : Actor
{
    [Editable] float maxHp = 100.0f;
    float hp = 0.0f;

    void BeginPlay() { hp = maxHp; }

    void OnBeginOverlap(Actor other) { TakeHit(25.0f); }

    void TakeHit(float amount)
    {
        hp = clamp(hp - amount, 0.0f, maxHp);
        if (hp <= 0.0f) DestroyActor();
    }
}
```

Uma barra de vida na tela: um Widget com Progress Bar ligada a HP / Max HP. Veja [Interface do jogo](article:game-ui).
--- en
A health variable, a function that takes health off, and the actor goes when it reaches zero. Here the damage comes from anything touching it.

```blueprint
Event BeginPlay -> Set HP = Max HP
Event ActorBeginOverlap -> Take Hit ( Amount = 25 )
Function Take Hit (Amount)
  -> Set HP = Clamp( HP - Amount, 0, Max HP )
  -> Branch ( HP <= 0 ) True -> Destroy Actor
```
```real
class Damageable extends Actor
    @editable
    var max_hp = 100.0
    var hp = 0.0

    event BeginPlay()
        hp = max_hp

    event OnBeginOverlap(other: Actor)
        TakeHit(25.0)

    func TakeHit(amount: float)
        hp = clamp(hp - amount, 0.0, max_hp)
        print("HP: {hp}")
        if hp <= 0.0
            DestroyActor()
```
```cs
public class DamageableCs : Actor
{
    [Editable] float maxHp = 100.0f;
    float hp = 0.0f;

    void BeginPlay() { hp = maxHp; }

    void OnBeginOverlap(Actor other) { TakeHit(25.0f); }

    void TakeHit(float amount)
    {
        hp = clamp(hp - amount, 0.0f, maxHp);
        if (hp <= 0.0f) DestroyActor();
    }
}
```

A health bar on the screen: a Widget with a Progress Bar bound to HP / Max HP. See [The game's UI](article:game-ui).
