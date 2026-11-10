id: water-rails
kind: recipe
title: Água e trilhos: barcos flutuando, trens no trilho | Water and rails: boats afloat, trains on track
keys: spline, pontos da spline, editar rio, editar trilho, alt arrastar, agua, water, water body, lago, lake, mar, sea, ondas, waves, correnteza, current, flutuar, float, boiar, trilho, rail, ferrovia, railway, trem, train, vagao, wagon, engatar, couple, locomotiva, locomotive, spline, bitola, gauge, manipulador, gizmo, setas, eixos, mover ponto no eixo, axis
--- pt
```diagram steps
Adicionar Rápido > Veículos > Corpo d'Água (ou Trilho) | Água: o tamanho é a escala; ondas e correnteza nos Detalhes | Trilho: os pontos nos Detalhes | Trem: Detalhes > Rail com o nome do trilho; vagões: Engatar em
```
## Água
O **Corpo d'Água** (Water Body) é uma superfície na altura do ator, do tamanho do seu plano. Nos Detalhes:
- **Ondas**: altura, comprimento e velocidade.
- **Correnteza** em X e Y.
- **Densidade** e **profundidade**.

Os barcos (e qualquer veículo com **Boias**) flutuam nela pelo volume submerso e são levados pela correnteza.

## Trilhos
O **Trilho** (Rail) é uma curva suave pelos seus pontos, aberta ou em circuito, desenhada com trilhos e dormentes.

Para pôr um trem nele, nos Detalhes do Veículo:
1. Em *Rail*, escreva o nome do trilho.
2. Em *Start Along Rail*, diga onde ele começa.
3. Num vagão, preencha *Couple To* (o veículo da frente) e *Coupling Gap* (a folga do engate).

A locomotiva puxa o trem inteiro: ela soma as massas e os freios de todos os vagões. Rampas no trilho também pesam.

```blueprint
Event BeginPlay -> Set Throttle Input ( Target, Throttle )
```
```real
class Locomotive extends Actor
    event BeginPlay()
        SetThrottleInput(0.6)
```
- **Editar no viewport:** com o rio ou o trilho selecionado, os pontos da spline aparecem como bolinhas amarelas. Arraste para mover (Shift: sobe e desce), **Alt** + arrastar cria um ponto novo, botão direito no ponto: adicionar ou apagar.
- **Manipulador do ponto:** clique num ponto da spline e aparecem **3 setas** (X vermelha, Y verde, Z azul), como o gizmo da Unreal: arraste uma seta para mover o ponto só naquele eixo. Arrastar o ponto em si continua livre (Shift: altura).

--- en
```diagram steps
Quick Add > Vehicles > Water Body (or Rail) | Water: its size is its scale; waves and current in its Details | Rail: its points in its Details | A train: Details > Rail with the rail's name; wagons: Couple To
```
## Water
A **Water Body** is a surface at the actor's height, the size of its plane. In its Details:
- **Waves**: height, length and speed.
- **Current** in X and Y.
- **Density** and **depth**.

Boats (and any vehicle with **Pontoons**) float on it by their submerged volume and drift with its current.

## Rails
A **Rail** is a smooth curve through its points, open or a loop, drawn with rails and sleepers.

To put a train on it, in the Vehicle's Details:
1. In *Rail*, write the rail's name.
2. In *Start Along Rail*, say where it starts.
3. On a wagon, fill *Couple To* (the vehicle ahead) and *Coupling Gap*.

The locomotive pulls the whole train: it adds up every wagon's mass and brakes. Slopes on the rail weigh in too.

```blueprint
Event BeginPlay -> Set Throttle Input ( Target, Throttle )
```
```real
class Locomotive extends Actor
    event BeginPlay()
        SetThrottleInput(0.6)
```
- **Edit in the viewport:** with the river or the rail selected, the spline's points show as yellow dots. Drag to move (Shift: up and down), **Alt** + drag makes a new point, right button on a point: add or delete.
- **Point gizmo:** click a spline point and **3 arrows** show (X red, Y green, Z blue), like Unreal's gizmo: drag an arrow to move the point along that axis only. Dragging the point itself stays free (Shift: height).
