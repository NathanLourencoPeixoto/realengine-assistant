id: structs-guide
kind: howto
title: Structs no código | Structs in code
keys: struct, structs, estrutura, dataclass, typedef struct, agrupar dados, tipo proprio, make struct, campo de struct
--- pt
```real
struct Hit
    var damage: int = 0
    var scale = 1.0
```
```cs
struct Hit { public int damage; public float scale; }
```
```py
@dataclass
class Hit:
    damage: int = 0
    scale: float = 1.0
```
```c
typedef struct { int damage; float scale; } Hit;
```
- Crie com `Hit(5, 2.0)` (C#: `new Hit(5, 2.0f)`; C: `Hit h = { 5, 2.0f };`), leia e mude campos (`h.damage += 3`).
- Viram estruturas de Blueprint: Blueprints também as usam. Até 16 campos.
--- en
```real
struct Hit
    var damage: int = 0
    var scale = 1.0
```
```cs
struct Hit { public int damage; public float scale; }
```
```py
@dataclass
class Hit:
    damage: int = 0
    scale: float = 1.0
```
```c
typedef struct { int damage; float scale; } Hit;
```
- Make one with `Hit(5, 2.0)` (C#: `new Hit(5, 2.0f)`; C: `Hit h = { 5, 2.0f };`), read and change fields (`h.damage += 3`).
- They become Blueprint structures: Blueprints use them too. Up to 16 fields.
