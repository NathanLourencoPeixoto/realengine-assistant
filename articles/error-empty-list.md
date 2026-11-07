id: error-empty-list
kind: error
title: Erro: [] vazio precisa do tipo | Error: an empty [] needs its type
keys: lista vazia, array vazio, empty list
match: An empty [] needs its type
--- pt
Um array vazio não diz de que é. Declare o tipo: `var nomes: string[] = []` (Real), `List<string> nomes = new List<string>();` (C#), `nomes: list[str] = []` (Python).
--- en
An empty array doesn't say what it holds. Declare its type: `var names: string[] = []` (Real), `List<string> names = new List<string>();` (C#), `names: list[str] = []` (Python).
