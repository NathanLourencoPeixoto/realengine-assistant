id: csharp-guide
kind: concept
title: C# na Real Engine: o que funciona | C# in the Real Engine: what works
keys: csharp, c#, c sharp, unity, monobehaviour, public class, using, foreach, list, var, new vector, editable, serializefield
--- pt
- `public class X : Actor { ... }` (ou `: Character`); `using` é ignorado; `MonoBehaviour` vira Actor.
- Campos com `[Editable]` ou `[SerializeField]` aparecem no Details.
- `void BeginPlay()`, `void Tick(float dt)`, `void OnBeginOverlap(Actor other)` (também `Start`, `Update`, `OnTriggerEnter`).
- `var`, `new Vector(...)`, `$"texto {x}"`, `for`, `foreach`, `while`, `switch`, `++`/`--`, casts `(int)x`, `struct`, `int[] xs = { ... }`.
- Não há classes extras, LINQ, genéricos próprios nem exceções: um arquivo é uma classe da engine.
--- en
- `public class X : Actor { ... }` (or `: Character`); `using` is ignored; `MonoBehaviour` becomes Actor.
- Fields with `[Editable]` or `[SerializeField]` show in Details.
- `void BeginPlay()`, `void Tick(float dt)`, `void OnBeginOverlap(Actor other)` (also `Start`, `Update`, `OnTriggerEnter`).
- `var`, `new Vector(...)`, `$"text {x}"`, `for`, `foreach`, `while`, `switch`, `++`/`--`, casts `(int)x`, `struct`, `int[] xs = { ... }`.
- There are no extra classes, LINQ, your own generics or exceptions: one file is one engine class.
