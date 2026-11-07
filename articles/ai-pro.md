id: ai-pro
kind: concept
title: IA a fundo: Behavior Tree, Blackboard, Real Brain | AI in depth: Behavior Tree, Blackboard, Real Brain
keys: ia, ai, behavior tree, arvore de comportamento, blackboard, real brain, utility ai, percepcao, ver o jogador, ouvir, navegacao, esquadrao, inimigo inteligente
--- pt
```diagram compare
 | Behavior Tree | Real Brain
Como decide | uma árvore de regras | uma nota por ação
Bom para | comportamentos claros | comportamentos que se misturam
Edita em | editor de árvore | editor de ações
```
- **Behavior Tree + Blackboard** (como na Unreal): sequências, seletores, decorators e tarefas; o Blackboard guarda alvo, posição, estado. **Run Behavior Tree** liga num Pawn.
- **Real Brain**: IA por utilidade (cada ação tem uma nota; a melhor vence), boa para comportamentos que se misturam.
- **Percepção:** visão e audição (**Report Noise Event**); previsão e interceptação de alvos.
- **Esquadrões** cercam o jogador; a dificuldade ajusta reação e mira; há depuração visual.
--- en
```diagram compare
 | Behavior Tree | Real Brain
How it decides | a tree of rules | a score per action
Good for | clear behaviors | blended behaviors
Edited in | the tree editor | the actions editor
```
- **Behavior Tree + Blackboard** (as in Unreal): sequences, selectors, decorators and tasks; the Blackboard keeps the target, a position, a state. **Run Behavior Tree** starts it on a Pawn.
- **Real Brain**: utility AI (each action gets a score; the best wins), good for blended behaviors.
- **Perception:** sight and hearing (**Report Noise Event**); predicting and intercepting targets.
- **Squads** encircle the player; difficulty tunes reaction and aim; there's visual debugging.
