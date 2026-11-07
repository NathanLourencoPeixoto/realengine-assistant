id: blueprint-or-code
kind: concept
title: Blueprint ou código? | Blueprint or code?
keys: blueprint ou codigo, qual usar, programar sem codigo, nao sei programar, visual ou texto, diferenca blueprint script, qual linguagem escolher
--- pt
```diagram compare
 | Blueprint | Código
Como se faz | ligar nós | escrever texto
Bom para começar | sim | sim
Lógica longa | cansa | sim
Roda em | a mesma VM + JIT | a mesma VM + JIT
Dá para misturar | sim | sim
```
- **Blueprint:** você liga nós com o mouse. Ótimo para começar e para quem pensa visualmente.
- **Código:** Real (a da engine, simples como Python), C#, Python ou C. Ótimo para lógica longa.
- **São a mesma coisa por baixo:** um script vira um grafo de Blueprint e roda no mesmo código nativo. Dá para misturar (um Blueprint pode herdar de um script).
- Aqui, as receitas aparecem do jeito que você escolher no topo da resposta (**Mostrar como**).
--- en
```diagram compare
 | Blueprint | Code
How | wire nodes | write text
Good to start | yes | yes
Long logic | tiring | yes
Runs on | the same VM + JIT | the same VM + JIT
Can be mixed | yes | yes
```
- **Blueprint:** you wire nodes with the mouse. Great to start and for visual thinkers.
- **Code:** Real (the engine's own, simple like Python), C#, Python or C. Great for long logic.
- **They're the same underneath:** a script becomes a Blueprint graph and runs on the same native code. You can mix them (a Blueprint can inherit from a script).
- Here, the recipes show the way you pick at the top of the answer (**Show as**).
