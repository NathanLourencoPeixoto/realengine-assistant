id: error-infinite-loop
kind: error
title: Erro: laço infinito interrompido | Error: an infinite loop was stopped
keys: laco infinito, travou, while true, infinite loop, nunca termina
match: an infinite loop
--- pt
Uma execução passou de 1 milhão de operações e foi parada (como na Unreal), para o editor não travar.
- Um `while` precisa de algo que mude a condição ou de um `break`.
- Trabalho longo e repetido? Use **Event Tick** (um pouco por quadro) ou **Set Timer by Event**.
--- en
A run went past 1 million operations and was stopped (as in Unreal), so the editor doesn't freeze.
- A `while` needs something that changes its condition, or a `break`.
- Long repeated work? Use **Event Tick** (a bit per frame) or **Set Timer by Event**.
