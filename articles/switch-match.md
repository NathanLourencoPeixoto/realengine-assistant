id: switch-match
kind: howto
title: switch e match | switch and match
keys: switch, match, case, escolher entre opcoes, varios ifs, select case, default, elif em cadeia
--- pt
```real
match state
    case 0
        print("parado")
    case 1, 2
        print("andando")
    else
        print("outro")
```
```cs
switch (state) { case 0: Idle(); break; case 1: case 2: Walk(); break; default: Other(); break; }
```
```py
match state:
    case 0:
        idle()
    case 1 | 2:
        walk()
    case _:
        other()
```
Cada caso roda só as suas linhas (o `break` final é opcional e um caso sem ele avisa).
--- en
```real
match state
    case 0
        print("idle")
    case 1, 2
        print("walking")
    else
        print("other")
```
```cs
switch (state) { case 0: Idle(); break; case 1: case 2: Walk(); break; default: Other(); break; }
```
```py
match state:
    case 0:
        idle()
    case 1 | 2:
        walk()
    case _:
        other()
```
Each case runs only its own lines (the final `break` is optional, and a case without one warns).
