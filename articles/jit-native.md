id: jit-native
kind: concept
title: Código nativo (JIT) de Blueprints e scripts | Native code (JIT) of Blueprints and scripts
keys: jit, nativo, native, compilacao nativa, performance de script, blueprint lento, vm, bytecode, interpretador, x64, sse, realengine_jit
--- pt
```diagram bars ms
Interpretado: 3.16
Nativo (JIT): 0.40
```
- Blueprints e scripts compilam para um **bytecode de registradores**; na primeira execução, um **JIT x64** transforma as operações numéricas (movimentos, saltos, aritmética, comparações, vetores) em código de máquina SSE.
- O resto (chamadas, eventos, strings, arrays) volta ao interpretador uma operação por vez: o comportamento é idêntico.
- Num laço aritmético de 40 mil voltas: 3,2 ms interpretado, 0,4 ms nativo (8×).
- `REALENGINE_JIT=0` desliga (para comparar ou isolar um problema).
--- en
```diagram bars ms
Interpreted: 3.16
Native (JIT): 0.40
```
- Blueprints and scripts compile to a **register bytecode**; on the first run, an **x64 JIT** turns the numeric operations (moves, jumps, arithmetic, comparisons, vectors) into SSE machine code.
- The rest (calls, events, strings, arrays) goes back to the interpreter one operation at a time: the behavior is identical.
- In an arithmetic loop of 40 thousand turns: 3.2 ms interpreted, 0.4 ms native (8×).
- `REALENGINE_JIT=0` turns it off (to compare or to isolate a problem).
