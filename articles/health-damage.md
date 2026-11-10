id: health-damage
kind: recipe
title: Vida e dano: Health, escudo, tipos de dano, morte | Health and damage: Health, shield, damage types, death
keys: vida, hp, dano, machucar, morrer, morte, health, damage, take damage, levar dano, perder vida, barra de vida, health bar, matar inimigo, health component, componente de vida, escudo, shield, armadura, armor, regeneracao, regenerar vida, regen, curar, heal, cura, reviver, revive, respawn, invencivel, invincible, god mode, tipo de dano, damage type, fogo, fire, veneno, poison, explosao, explosion, dano radial, radial damage, dano em area, granada, grenade, multiplicador de dano, resistencia, fraqueza, imune, numeros de dano, damage numbers, dano flutuante, ragdoll ao morrer, apply damage, apply radial damage, event anydamage, on death, on healed, on shield broken, get health percent, is dead
--- pt
Como o **Health Component** dos jogos da Unreal, pronto: **Details > Adicionar > Vida** (no nível ou no Blueprint, em **Componentes > + Adicionar > Jogabilidade**).
1. **Vida Máxima** e **Vida**; **Escudo Máximo**: o escudo recebe o dano antes da vida.
2. **Regeneração**: depois de **Atraso da Regeneração** segundos sem dano, a vida e o escudo voltam na taxa de cada um.
3. **Multiplicadores de Dano**: um tipo de dano é uma **Gameplay Tag** (`Damage.Fire`, `Damage.Physical`...) com o quanto o ator recebe (0 imune, 0,5 metade, 2 o dobro). Vale o mais específico: `Damage` cobre `Damage.Fire.Burning`, mas `Damage.Fire` ganha dele.
4. **Ao Morrer**: **Só o Evento**, **Destruir o Ator** (depois do atraso) ou **Ragdoll** (a Skeletal Mesh com Physics Asset vira boneco de pano).
5. **Números de Dano** sobem sobre o ator; **Mostrar Barra de Vida** no personagem do jogador põe o **WBP_HealthBar** (em Content/UI, criado ao adicionar a Vida) na tela. Ele também vai no seu jogo com **Create Widget** + **Add to Viewport**.

Nós (categoria **Game > Damage**): **Apply Damage**, **Apply Radial Damage** (explosão com queda pela distância), **Heal**, **Get Health**, **Get Health Percent**, **Get Max Health**, **Get Shield**, **Set Max Health**, **Set Shield**, **Is Dead**, **Revive**, **Set Invincible**, **Set Damage Multiplier**. Eventos do ator: **Event AnyDamage** (dano, tipo, quem e com o quê), **Event On Healed**, **Event On Death**, **Event On Shield Broken**.

```diagram steps
Inimigo: Details > Adicionar > Vida | Armadilha: OnActorBeginOverlap -> Apply Damage (Damage.Fire) | Vida chega a 0: Event On Death | Ao Morrer: Ragdoll ou Destruir o Ator
```
```blueprint
Event ActorBeginOverlap -> Apply Damage ( Target = Other Actor, Amount = 25, Damage Type = "Damage.Fire", Instigator = self )
Event AnyDamage -> Print String ( Format Text ( "dano {0} de {1}", Damage, Damage Type ) )
Event On Death -> Apply Radial Damage ( Base Damage = 80, Origin = Get Actor Location, Damage Radius = 400, Damage Type = "Damage.Explosion" )
```
```real
class Barrel extends Actor
    event BeginPlay()
        SetDamageMultiplier("Damage.Fire", 2.0)

    event OnAnyDamage(damage: float, damage_type: string, instigator: Actor, causer: Actor)
        print("dano: {damage} ({damage_type})")

    event OnDeath(killer: Actor, damage_type: string, causer: Actor)
        ApplyRadialDamage(80.0, GetActorLocation(), 400.0, "Damage.Explosion", killer, self, 1.0, 0.0)
```
```cs
public class FireTrap : Actor
{
    void OnBeginOverlap(Actor other)
    {
        other.ApplyDamage(25.0f, "Damage.Fire", this, this);
    }
}
```

O custo: 1000 atores levando dano todo quadro custam ~0,11 ms; a lista **Health and Damage** do Debug Viewer (F10) mostra o tempo e a vida de cada ator. Para montar a sua própria barra, veja [Interface do jogo](article:game-ui).
--- en
Like the **Health Component** of Unreal's games, ready: **Details > Add > Health** (in the level, or in a Blueprint under **Components > + Add > Gameplay**).
1. **Max Health** and **Health**; **Max Shield**: the shield takes the damage before the health.
2. **Regeneration**: after **Regen Delay** seconds without damage, the health and the shield come back at their rates.
3. **Damage Multipliers**: a damage type is a **Gameplay Tag** (`Damage.Fire`, `Damage.Physical`...) with how much the actor takes (0 immune, 0.5 half, 2 double). The most specific wins: `Damage` covers `Damage.Fire.Burning`, but `Damage.Fire` beats it.
4. **On Death**: **Only the Event**, **Destroy Actor** (after the delay) or **Ragdoll** (the Skeletal Mesh with a Physics Asset goes limp).
5. **Damage Numbers** float up over the actor; **Show Health Bar** on the player's pawn puts **WBP_HealthBar** (in Content/UI, made when the Health is added) on the screen. It goes into your own game too with **Create Widget** + **Add to Viewport**.

Nodes (category **Game > Damage**): **Apply Damage**, **Apply Radial Damage** (an explosion falling off with the distance), **Heal**, **Get Health**, **Get Health Percent**, **Get Max Health**, **Get Shield**, **Set Max Health**, **Set Shield**, **Is Dead**, **Revive**, **Set Invincible**, **Set Damage Multiplier**. The actor's events: **Event AnyDamage** (damage, type, who and with what), **Event On Healed**, **Event On Death**, **Event On Shield Broken**.

```diagram steps
Enemy: Details > Add > Health | Trap: OnActorBeginOverlap -> Apply Damage (Damage.Fire) | Health reaches 0: Event On Death | On Death: Ragdoll or Destroy Actor
```
```blueprint
Event ActorBeginOverlap -> Apply Damage ( Target = Other Actor, Amount = 25, Damage Type = "Damage.Fire", Instigator = self )
Event AnyDamage -> Print String ( Format Text ( "damage {0} of {1}", Damage, Damage Type ) )
Event On Death -> Apply Radial Damage ( Base Damage = 80, Origin = Get Actor Location, Damage Radius = 400, Damage Type = "Damage.Explosion" )
```
```real
class Barrel extends Actor
    event BeginPlay()
        SetDamageMultiplier("Damage.Fire", 2.0)

    event OnAnyDamage(damage: float, damage_type: string, instigator: Actor, causer: Actor)
        print("damage: {damage} ({damage_type})")

    event OnDeath(killer: Actor, damage_type: string, causer: Actor)
        ApplyRadialDamage(80.0, GetActorLocation(), 400.0, "Damage.Explosion", killer, self, 1.0, 0.0)
```
```cs
public class FireTrap : Actor
{
    void OnBeginOverlap(Actor other)
    {
        other.ApplyDamage(25.0f, "Damage.Fire", this, this);
    }
}
```

The cost: 1000 actors damaged every frame take ~0.11 ms; the Debug Viewer's (F10) **Health and Damage** list shows the time and each actor's health. To make a bar of your own, see [The game's UI](article:game-ui).
