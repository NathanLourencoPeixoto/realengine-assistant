id: blueprint-functions
kind: howto
title: Funções, macros e Custom Events nos Blueprints | Functions, macros and Custom Events in Blueprints
keys: funcao blueprint, function, custom event, evento personalizado, chamar evento, return node, parametros, entrada saida, macro, reutilizar logica
--- pt
- **Função**: entradas e saídas (Return Node), roda na hora. Crie no painel My Blueprint > Functions.
- **Custom Event**: sem retorno; pode ser chamado pelo nome por widgets, Sequencer, timers, notifies e outros Blueprints. Aceita **Delay** dentro.
- Funções puras (sem pino branco) são para cálculos; as outras têm efeito.
- Em código: um método sem parâmetros e sem retorno vira Custom Event; com parâmetros ou retorno vira função.
--- en
- **Function**: inputs and outputs (Return Node), runs at once. Make one in My Blueprint > Functions.
- **Custom Event**: no return; can be called by name from widgets, the Sequencer, timers, notifies and other Blueprints. It allows a **Delay** inside.
- Pure functions (no white pin) are for computing; the others have effects.
- In code: a method without parameters and return becomes a Custom Event; with parameters or a return, a function.
