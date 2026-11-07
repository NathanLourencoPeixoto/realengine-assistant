id: error-not-declared
kind: error
title: Erro: 'x' isn't declared here | Error: 'x' isn't declared here
keys: nao declarado, nao existe, variavel desconhecida, undeclared, not declared
match: isn't declared here
--- pt
O nome não existe onde foi usado.
- Erro de digitação? Os nomes diferenciam maiúsculas (`Speed` não é `speed`).
- Variável de outro método? Cada evento tem as suas locais; para guardar entre eventos, declare um **campo** da classe (`var x = 0` no topo, em Real).
- Uma função da engine? Confira o nome na [referência da API](open:api); **Ctrl+Espaço** completa.
--- en
The name doesn't exist where it's used.
- A typo? Names are case-sensitive (`Speed` isn't `speed`).
- A variable of another method? Each event has its own locals; to keep a value between events, declare a class **field** (`var x = 0` at the top, in Real).
- An engine function? Check its name in the [API reference](open:api); **Ctrl+Space** completes it.
