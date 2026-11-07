id: print-debug
kind: recipe
title: Mostrar valores na tela (depurar) | Show values on the screen (debugging)
keys: print, imprimir, mostrar valor, debug, depurar, console, log, ver variavel, print string, por que nao funciona, testar valor
--- pt
O texto aparece no canto da tela durante o Play e no Registro de Saída. Coloque valores entre chaves na interpolação.

```blueprint
Event BeginPlay
  -> Print String ( In String = Append( "Posição: ", To String( Get Actor Location ) ) )
```
```real
class Debugger extends Actor
    var hits = 3

    event BeginPlay()
        print("Hits: {hits}, at {GetActorLocation()}")
```
```cs
public class DebuggerCs : Actor
{
    int hits = 3;

    void BeginPlay()
    {
        print($"Hits: {hits}, at {GetActorLocation()}");
    }
}
```
```py
class DebuggerPy(Actor):
    hits = 3

    def begin_play(self):
        print(f"Hits: {self.hits}, at {get_actor_location()}")
```

Também: **F10** abre o Debug Viewer (o custo de cada objeto) e **Janela > Registro de Saída** guarda tudo. [Abrir o registro](open:log)
--- en
The text shows in the screen's corner while playing and in the Output Log. Put values between braces in the interpolation.

```blueprint
Event BeginPlay
  -> Print String ( In String = Append( "Location: ", To String( Get Actor Location ) ) )
```
```real
class Debugger extends Actor
    var hits = 3

    event BeginPlay()
        print("Hits: {hits}, at {GetActorLocation()}")
```
```cs
public class DebuggerCs : Actor
{
    int hits = 3;

    void BeginPlay()
    {
        print($"Hits: {hits}, at {GetActorLocation()}");
    }
}
```
```py
class DebuggerPy(Actor):
    hits = 3

    def begin_play(self):
        print(f"Hits: {self.hits}, at {get_actor_location()}")
```

Also: **F10** opens the Debug Viewer (each object's cost) and **Window > Output Log** keeps everything. [Open the log](open:log)
