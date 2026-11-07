id: arrays-loops
kind: howto
title: Arrays e laços | Arrays and loops
keys: array, arrays, lista, list, laco, loop, for, foreach, while, percorrer lista, adicionar na lista, add, remove, contains, length, len, indice
--- pt
```real
var xs = [3, 4, 5]
xs.Add(6)
for x in xs
    print("{x}")
for i in 0..len(xs)
    xs[i] = xs[i] * 2
```
```cs
List<int> xs = new List<int>();
xs.Add(3);
foreach (int x in xs) print($"{x}");
```
```py
xs = [3, 4, 5]
xs.append(6)
for x in xs:
    print(f"{x}")
```
- Métodos: `Add`/`append`, `Remove`, `RemoveAt`, `Contains`, `IndexOf`, `Insert`, `Clear`, `Count`/`len`, `Shuffle`; `a[i]` e `a[i] = v`.
- `break` e `continue` funcionam; um `while` precisa de algo que mude a condição.
--- en
```real
var xs = [3, 4, 5]
xs.Add(6)
for x in xs
    print("{x}")
for i in 0..len(xs)
    xs[i] = xs[i] * 2
```
```cs
List<int> xs = new List<int>();
xs.Add(3);
foreach (int x in xs) print($"{x}");
```
```py
xs = [3, 4, 5]
xs.append(6)
for x in xs:
    print(f"{x}")
```
- Methods: `Add`/`append`, `Remove`, `RemoveAt`, `Contains`, `IndexOf`, `Insert`, `Clear`, `Count`/`len`, `Shuffle`; `a[i]` and `a[i] = v`.
- `break` and `continue` work; a `while` needs something that changes its condition.
