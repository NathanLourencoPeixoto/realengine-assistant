id: blueprints-basics
kind: howto
title: Blueprints: o básico | Blueprints: the basics
keys: blueprint, nos, programacao visual, evento, begin play, tick, variavel, funcao, classe, grafo, visual scripting
--- pt
```diagram steps
Adicionar > Blueprint Class | Escolher o pai | Event Graph: eventos e nós | Compile | Arrastar para o nível
```
1. Navegador de Conteúdo: **Adicionar > Blueprint Class** e escolha o pai (Actor, Character, Pawn...).
2. Duplo clique abre o editor (como o da Unreal): Viewport, Construction Script e o **Event Graph**.
3. Clique com o botão direito no grafo para adicionar nós; ligue os pinos brancos (execução) a partir de um evento: **Event BeginPlay** (ao começar) ou **Event Tick** (todo quadro).
4. Variáveis ficam no painel da esquerda; marque **Instance Editable** para editá-las no Details de cada ator.
5. **Compile** e arraste a classe para o nível.

Prefere código? Veja [Scripts](article:scripts-basics).
--- en
```diagram steps
Add > Blueprint Class | Pick the parent | Event Graph: events and nodes | Compile | Drag into the level
```
1. Content Browser: **Add > Blueprint Class** and pick the parent (Actor, Character, Pawn...).
2. Double-click opens its editor (like Unreal's): Viewport, Construction Script and the **Event Graph**.
3. Right-click the graph to add nodes; wire the white pins (execution) from an event: **Event BeginPlay** (at the start) or **Event Tick** (every frame).
4. Variables are on the left panel; check **Instance Editable** to edit them in each actor's Details.
5. **Compile** and drag the class into the level.

Prefer code? See [Scripts](article:scripts-basics).
