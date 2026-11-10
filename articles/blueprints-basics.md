id: blueprints-basics
kind: howto
title: Blueprints: o básico | Blueprints: the basics
keys: blueprint, nos, programacao visual, evento, begin play, tick, variavel, funcao, classe, grafo, visual scripting, pino de asset, asset pin, sequencia por variavel, som por variavel, trocar sequencia, modular, variavel no lugar do valor
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
- **Tudo é pino:** o asset ou nome que um nó usa (a **Sequence** do Play Sequence, o **Sound** do Play Sound, o **System** das partículas, o **Widget Name**, a **Key Name** do Blackboard, o **Montage**...) é também um **pino de entrada** do tipo Name: o valor do Details aparece nele, e ligando uma variável (Name ou String) o nó usa o asset que ela tiver na hora. O delegate do Custom Event fica no **título** do nó, como na Unreal.

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
- **Everything is a pin:** the asset or name a node uses (Play Sequence's **Sequence**, Play Sound's **Sound**, the particles' **System**, the **Widget Name**, the Blackboard's **Key Name**, the **Montage**...) is also a Name **input pin**: the Details value shows in it, and wiring a variable (Name or String) makes the node use whatever asset it holds then. The Custom Event's delegate sits in the node's **title**, as in Unreal.
