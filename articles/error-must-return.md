id: error-must-return
kind: error
title: Erro: a função precisa retornar um valor | Error: the function must return a value
keys: retorno, return, falta return, must return
match: must return
--- pt
A função declara um tipo de retorno (`-> int`), mas algum caminho termina sem `return`. Garanta um `return` no fim, também depois de um `if` sem `else`.
--- en
The function declares a return type (`-> int`), but some path ends without a `return`. Make sure there's a `return` at the end, also after an `if` without an `else`.
