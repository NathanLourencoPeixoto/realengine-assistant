id: blueprint-debug
kind: howto
title: Depurar Blueprints | Debug Blueprints
keys: depurar blueprint, debug blueprint, nao funciona, nao roda, blueprint nao faz nada, compile error, erro de compilacao, print string
--- pt
1. **Compile** e veja os erros no painel de baixo (o nó com problema fica marcado).
2. Coloque **Print String** nos caminhos para ver o que roda.
3. O evento roda? Confira se o ator está no nível, se é da classe certa e, para overlaps, se tem colisão.
4. Laço que trava? Uma execução passa de 1 milhão de operações e é parada com uma mensagem. [Laço infinito](article:error-infinite-loop)
--- en
1. **Compile** and read the errors in the bottom panel (the faulty node is marked).
2. Put **Print String** on the paths to see what runs.
3. Does the event run? Check the actor is in the level, of the right class and, for overlaps, that it has collision.
4. A loop that hangs? A run past 1 million operations is stopped with a message. [Infinite loop](article:error-infinite-loop)
