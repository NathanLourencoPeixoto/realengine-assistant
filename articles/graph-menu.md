id: graph-menu
kind: howto
title: Menu do botão direito nos gráficos | The right-click menu in graphs
keys: arrastar variavel, arrastar funcao, arrastar componente, drag variable, drag function, drag component, get component, categorias, caixas, botao direito, right click, menu de nos, node menu, all actions, todas as acoes, recentes, recent, recomendados, recommended, sugestao de no, sugestões, historico, history, context sensitive, sensivel ao contexto, adicionar no, add node, blueprint, animgraph, material, behavior tree, sound cue, particulas
--- pt
```diagram steps
Botão direito no gráfico (ou solte um fio no vazio) | Recentes: as 2 últimas que você usou | Recomendados: 2 que conectam com o que você está fazendo | Depois, só as ações que este gráfico aceita
```
## Como funciona
Em todo gráfico (Blueprint, Função, Macro, Construction Script, AnimGraph, Material, Behavior Tree, Sound Cue e Sistema de Partículas), o **botão direito** abre o menu de nós:
- **Recentes**: as **2 últimas** ações que você usou nesse tipo de gráfico (guardadas entre sessões).
- **Recomendados**: **2 ações** que costumam vir depois do que você está fazendo: o nó do fio que você puxou, o nó selecionado ou o último que você colocou. Ex.: depois de **Event BeginPlay**, *Print String* e *Delay*; depois de **Get Actor Location**, *Set Actor Location*.
- O menu **aprende**: o que você coloca depois de um nó passa a ser recomendado depois dele.
- **Só o que o gráfico aceita**: numa **função** não aparecem eventos nem nós latentes (Delay); no **Construction Script** também não; os nós de **Animation Blueprint** só num Animation Blueprint. Puxando um fio, só o que encaixa nele.
- Digitar na busca mostra todas as ações do gráfico que batem com o texto.
- As ações ficam em **caixas por categoria que abrem e fecham** (Flow Control, Utilities > Time...), como na Unreal; buscando, as caixas abrem sozinhas com só o que bate.
- **Arrastar do My Blueprint:** variáveis (Ctrl Get, Alt Set), **funções** (vira a chamada), **macros** e, do painel Components, um **componente** (vira *Get <componente>*).
--- en
```diagram steps
Right click the graph (or drop a wire on empty space) | Recent: the last 2 you used | Recommended: 2 that connect with what you are doing | Then only the actions this graph takes
```
## How it works
In every graph (Blueprint, Function, Macro, Construction Script, AnimGraph, Material, Behavior Tree, Sound Cue and Particle System), the **right button** opens the node menu:
- **Recent**: the **last 2** actions you used in that kind of graph (kept between sessions).
- **Recommended**: **2 actions** that usually come after what you are doing: the node of the wire you dragged, the selected node or the last one you placed. E.g. after **Event BeginPlay**, *Print String* and *Delay*; after **Get Actor Location**, *Set Actor Location*.
- The menu **learns**: what you place after a node becomes recommended after it.
- **Only what the graph takes**: a **function** shows no events and no latent nodes (Delay); neither does the **Construction Script**; **Animation Blueprint** nodes only in one. Dragging a wire, only what fits it.
- Typing in the search shows every action of the graph that matches.
- Actions sit in **category boxes that open and close** (Flow Control, Utilities > Time...), as in Unreal; searching opens the boxes with only the matches.
- **Drag from My Blueprint:** variables (Ctrl Get, Alt Set), **functions** (a call), **macros** and, from the Components panel, a **component** (a *Get <component>*).
