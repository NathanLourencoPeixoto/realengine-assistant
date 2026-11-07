id: real-language
kind: concept
title: A linguagem Real: guia rápido | The Real language: quick guide
keys: linguagem real, real language, sintaxe real, var, func, event, extends, editable, elif, for in, intervalo, sintaxe, cheat sheet, guia da linguagem
--- pt
```real
class Door extends Actor          # um script = uma classe
    @editable                     # aparece no Details
    var speed: float = 90         # tipo opcional (inferido)
    var open = false

    event BeginPlay()             # BeginPlay, Tick(dt), OnBeginOverlap(other)...
        for i in 0..10            # 0..9 ("..=" inclui o 10; "step 2")
            print("i = {i}")
        Toggle()

    event Toggle()                # Custom Event (chamável pelo nome)
        open = not open

    func Twice(x: int) -> int     # função com retorno
        return x * 2
```
- Blocos por indentação; `if` / `elif` / `else`, `while`, `for x in array`, `match` / `case`.
- `and` / `or` / `not` (também `&&` `||` `!`); comentários `#` e `//`; textos com `{interpolação}`.
- Arrays `[1, 2, 3]`, structs com `struct`, toda a API da engine como funções.
--- en
```real
class Door extends Actor          # one script = one class
    @editable                     # shows in Details
    var speed: float = 90         # the type is optional (inferred)
    var open = false

    event BeginPlay()             # BeginPlay, Tick(dt), OnBeginOverlap(other)...
        for i in 0..10            # 0..9 ("..=" includes 10; "step 2")
            print("i = {i}")
        Toggle()

    event Toggle()                # Custom Event (callable by name)
        open = not open

    func Twice(x: int) -> int     # a function with a return
        return x * 2
```
- Blocks by indentation; `if` / `elif` / `else`, `while`, `for x in array`, `match` / `case`.
- `and` / `or` / `not` (also `&&` `||` `!`); comments `#` and `//`; texts with `{interpolation}`.
- Arrays `[1, 2, 3]`, structs with `struct`, the whole engine API as functions.
