id: scripts-basics
kind: howto
title: Scripts em Real, C#, Python e C | Scripts in Real, C#, Python and C
keys: script, codigo, programar, csharp, c#, python, linguagem real, editor de codigo, ide, programacao, classe em codigo
--- pt
```diagram steps
Adicionar > Script | Escolher a linguagem | Escrever (Ctrl+Espaço completa) | Ctrl+S compila | Arrastar para o nível
```
1. Navegador de Conteúdo: **Adicionar > Script** e escolha a linguagem: **Real** (a da engine), **C#**, **Python** ou **C**.
2. Duplo clique abre o **Editor de Código**: cores, completar (**Ctrl+Espaço**), erros enquanto digita, **F12** vai à definição, **F1** abre a referência da API.
3. **Ctrl+S** salva e compila. O script é uma classe: arraste-o para o nível como um Blueprint.

Toda a API da engine está disponível: cada nó de Blueprint é uma função (`Play Sound 2D` → `PlaySound2D`). [Abrir a referência](open:api)

```real
class Hello extends Actor
    event BeginPlay()
        print("Olá, {GetActorLocation()}")
```
--- en
```diagram steps
Add > Script | Pick the language | Write (Ctrl+Space completes) | Ctrl+S compiles | Drag into the level
```
1. Content Browser: **Add > Script** and pick the language: **Real** (the engine's own), **C#**, **Python** or **C**.
2. Double-click opens the **Code Editor**: colors, completion (**Ctrl+Space**), errors as you type, **F12** goes to the definition, **F1** opens the API reference.
3. **Ctrl+S** saves and compiles. The script is a class: drag it into the level like a Blueprint.

The whole engine API is there: every Blueprint node is a function (`Play Sound 2D` → `PlaySound2D`). [Open the reference](open:api)

```real
class Hello extends Actor
    event BeginPlay()
        print("Hello, {GetActorLocation()}")
```
