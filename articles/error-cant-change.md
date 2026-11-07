id: error-cant-change
kind: error
title: Erro: não pode ser mudado aqui | Error: can't be changed here
keys: parametro somente leitura, variavel do laco, readonly, cant change
match: can't be changed here
--- pt
Parâmetros e a variável de um `for` são somente leitura. Copie para uma local e mude a cópia:
```real
var passo = i
passo += 2
```
--- en
Parameters and a `for` loop's variable are read-only. Copy it into a local and change the copy:
```real
var step = i
step += 2
```
