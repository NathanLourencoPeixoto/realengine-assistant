id: python-guide
kind: concept
title: Python na Real Engine: o que funciona | Python in the Real Engine: what works
keys: python, py, def, self, snake_case, dataclass, f-string, range, class python, begin_play, tick
--- pt
- `class X(Actor):` (ou `Character`); atributos da classe ou `self.x = v` no `__init__` viram campos.
- `def begin_play(self):`, `def tick(self, dt):`, `def on_begin_overlap(self, other):`.
- A API em snake_case: `play_sound_2d`, `get_actor_location` (ou em PascalCase, como preferir).
- `for i in range(...)`, `while`, `match` / `case`, f-strings, `a if c else b`, `**`, `//`, listas `[1, 2]`, `@dataclass` para structs.
- É Python compilado para a VM da engine: sem `import` de bibliotecas, sem `numpy`.
--- en
- `class X(Actor):` (or `Character`); class attributes or `self.x = v` in `__init__` become fields.
- `def begin_play(self):`, `def tick(self, dt):`, `def on_begin_overlap(self, other):`.
- The API in snake_case: `play_sound_2d`, `get_actor_location` (or PascalCase, as you like).
- `for i in range(...)`, `while`, `match` / `case`, f-strings, `a if c else b`, `**`, `//`, lists `[1, 2]`, `@dataclass` for structs.
- It's Python compiled for the engine's VM: no library `import`s, no `numpy`.
