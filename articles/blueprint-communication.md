id: blueprint-communication
kind: howto
title: Um Blueprint falar com outro (Cast, interfaces, dispatchers) | One Blueprint talking to another (Cast, interfaces, dispatchers)
keys: comunicacao entre blueprints, chamar outro blueprint, cast to, interface, event dispatcher, referencia de outro ator, falar com outro ator, get all actors of class, pegar referencia
--- pt
- **Cast To**: "este ator é da classe X?" Se for, você acessa as variáveis e funções dele.
- **Interface**: um contrato de funções que várias classes implementam (Interagir, Levar Dano). Chame sem saber a classe.
- **Event Dispatcher**: um ator avisa ("morri"), quem estiver ligado (Bind) reage.
- Para achar atores: **Get Player Character**, **Get All Actors of Class**, o ator do overlap ou uma variável Actor preenchida no Details.
--- en
- **Cast To**: "is this actor of class X?" If it is, you reach its variables and functions.
- **Interface**: a contract of functions many classes implement (Interact, Take Damage). Call it without knowing the class.
- **Event Dispatcher**: an actor announces ("I died"), whoever is bound (Bind) reacts.
- To find actors: **Get Player Character**, **Get All Actors of Class**, the overlap's actor or an Actor variable filled in Details.
