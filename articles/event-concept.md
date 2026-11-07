id: event-concept
kind: concept
title: Eventos: BeginPlay, Tick, Overlap | Events: BeginPlay, Tick, Overlap
keys: evento, eventos, beginplay, tick, overlap, quando comeca, todo quadro, quando encosta, event, events, callback, o que e tick
--- pt
```diagram steps
BeginPlay: uma vez, ao começar | Tick: todo quadro | Overlap: quando algo encosta | Custom Event: quando você chamar
```
Um evento é **quando** algo roda:
- **BeginPlay** (em código: `BeginPlay`, `Start`, `_ready`): uma vez, quando o ator começa.
- **Tick** (`Tick`, `Update`): todo quadro, com o tempo do quadro (`dt`). Use para movimento contínuo.
- **ActorBeginOverlap / EndOverlap** (`OnBeginOverlap`, `OnTriggerEnter`): quando algo encosta / sai.
- **Custom Event**: um evento seu, chamado pelo nome (por widgets, sequências, timers ou outro código).
- Teclas e ações de entrada também viram eventos nos Blueprints.
--- en
```diagram steps
BeginPlay: once, at the start | Tick: every frame | Overlap: when something touches | Custom Event: when you call it
```
An event is **when** something runs:
- **BeginPlay** (in code: `BeginPlay`, `Start`, `_ready`): once, when the actor starts.
- **Tick** (`Tick`, `Update`): every frame, with the frame's time (`dt`). Use it for continuous movement.
- **ActorBeginOverlap / EndOverlap** (`OnBeginOverlap`, `OnTriggerEnter`): when something touches / leaves.
- **Custom Event**: your own event, called by name (by widgets, sequences, timers or other code).
- Keys and input actions are events in Blueprints too.
