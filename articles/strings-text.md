id: strings-text
kind: howto
title: Textos: juntar, formatar, converter | Texts: join, format, convert
keys: string, texto, juntar texto, concatenar, formatar, interpolacao, fstring, numero para texto, to string, upper, lower, replace, substring
--- pt
- Interpolação: `"Vida: {hp}"` (Real), `$"Vida: {hp}"` (C#), `f"Vida: {self.hp}"` (Python).
- Juntar: `"a" + "b"`; número para texto: `str(x)`; texto para número: `int(s)`, `float(s)`.
- Métodos: `ToUpper`, `ToLower`, `Contains`, `Replace`, `Substring`, `Length`.
- Em Blueprint: **Append**, **To String**, **Format Text** (o texto com `{0}` `{1}` `{2}` `{3}` trocados pelas entradas: "Pontos: {0} / {1}"; qualquer valor ligado vira texto; `{{` escreve uma chave).
--- en
- Interpolation: `"Health: {hp}"` (Real), `$"Health: {hp}"` (C#), `f"Health: {self.hp}"` (Python).
- Join: `"a" + "b"`; number to text: `str(x)`; text to number: `int(s)`, `float(s)`.
- Methods: `ToUpper`, `ToLower`, `Contains`, `Replace`, `Substring`, `Length`.
- In a Blueprint: **Append**, **To String**, **Format Text** (the text with `{0}` `{1}` `{2}` `{3}` replaced by the inputs: "Score: {0} / {1}"; any value wired in turns to text; `{{` writes a brace).
