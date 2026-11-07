id: score-counter
kind: recipe
title: Contar pontos | Count points
keys: pontos, pontuacao, placar, score, contar moedas, somar pontos, highscore, contador
--- pt
Cada vez que algo encosta, soma um ponto. Para mostrar na tela, ligue o valor a um Text de um Widget.

```blueprint
Event ActorBeginOverlap
  -> Set Score = Score + 1
  -> Print String ( Append( "Pontos: ", To String( Score ) ) )
```
```real
class ScoreZone extends Actor
    var score = 0

    event OnBeginOverlap(other: Actor)
        score += 1
        print("Score: {score}")
```
```py
class ScoreZonePy(Actor):
    score = 0

    def on_begin_overlap(self, other: Actor):
        self.score += 1
        print(f"Score: {self.score}")
```
--- en
Each time something touches it, a point is added. To show it, bind the value to a Widget's Text.

```blueprint
Event ActorBeginOverlap
  -> Set Score = Score + 1
  -> Print String ( Append( "Score: ", To String( Score ) ) )
```
```real
class ScoreZone extends Actor
    var score = 0

    event OnBeginOverlap(other: Actor)
        score += 1
        print("Score: {score}")
```
```py
class ScoreZonePy(Actor):
    score = 0

    def on_begin_overlap(self, other: Actor):
        self.score += 1
        print(f"Score: {self.score}")
```
