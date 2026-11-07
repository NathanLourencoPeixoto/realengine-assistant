id: vehicles
kind: recipe
title: Veículos: carros, motos, tanques, barcos, trens, aviões e helicópteros | Vehicles: cars, motorcycles, tanks, boats, trains, airplanes and helicopters
keys: veiculo, vehicle, carro, car, moto, motorcycle, caminhao, truck, tanque, tank, barco, boat, trem, train, aviao, airplane, plane, helicoptero, helicopter, dirigir, drive, pilotar, fly, chaos vehicle, wheeled vehicle, acelerador, throttle, freio, brake, marcha, gear, cambio, gearbox, entrar no carro, enter vehicle, sair do carro, exit vehicle, jogo de corrida, racing game, jogo de carro, car game
--- pt
```diagram steps
Adicionar Rápido > Veículos > Veículo (um modelo) | Detalhes: Possuir Automaticamente (ou Enter Vehicle no Blueprint) | Play: W/S acelera e freia, A/D vira, Espaço freio de mão, F portas | Duplo clique no asset: chassi, marchas e peças
```
## Como funciona
Um **Veículo** (`.rvehicle`) é um **chassi** (massa, centro de massa, caixa de colisão, arrasto) mais **peças**. Os 10 modelos já andam como estão: Carro, Carro Esportivo, Caminhão 6x6 (com caçamba basculante), Moto, Tanque (esteiras), Barco, Locomotiva, Vagão, Avião e Helicóptero.

A física é própria e profissional:
- **Suspensão por raio** com mola, amortecedor e barra estabilizadora.
- **Pneus pela fórmula mágica**, com deslizamento, ângulo de deriva e elipse de atrito; controle de tração e ABS.
- **Motor** com curva de torque, embreagem que patina na saída e limitador.
- **Câmbio** automático ou manual, e **diferencial** aberto, travado ou autoblocante.
- **Por tipo de veículo**: esteiras que giram no lugar (tanque); a moto se inclina sozinha na curva; flutuação, hélice e leme (barco); asas com estol e superfícies de controle (avião); rotor com coletivo, cíclico e estabilidade que paira ao soltar (helicóptero).

Comandos do jogador:

| Veículo | Comandos |
|---|---|
| Carro, moto, caminhão, tanque | **W/S** acelera; S freia e depois dá ré. **A/D** vira. **Espaço** freio de mão. **F/G/H/J** abrem as peças (portas, capô, caçamba). |
| Avião e helicóptero | **W/S** arfagem. **A/D** rolagem. **Q/E** guinada. **Shift/Ctrl** acelerador (avião) ou coletivo (helicóptero). |

```blueprint
Event BeginPlay -> Enter Vehicle ( Target )
```
```real
class Driver extends Actor
    event Tick(dt: float)
        SetThrottleInput(1)
        SetSteeringInput(0.3)
```
Outros nós: *Set Brake Input*, *Set Handbrake Input*, *Set Flight Input*, *Set Gear*, *Set Engine On*, *Set Part Position*, *Toggle Part*, *Exit Vehicle*, *Get Engine RPM*, *Get Current Gear*. Veja também [Peças de veículo](article:vehicle-parts) e [Água e trilhos](article:water-rails).
--- en
```diagram steps
Quick Add > Vehicles > Vehicle (a template) | Details: Auto Possess (or Enter Vehicle in a Blueprint) | Play: W/S throttle and brake, A/D steer, Space handbrake, F doors | Double-click the asset: chassis, gears and parts
```
## How it works
A **Vehicle** (`.rvehicle`) is a **chassis** (mass, center of mass, collision box, drag) plus **parts**. The 10 templates drive as they are: Car, Sports Car, Truck 6x6 (with a dump bed), Motorcycle, Tank (tracks), Boat, Locomotive, Train Wagon, Airplane and Helicopter.

The physics is its own, and professional:
- **Raycast suspension** with springs, dampers and anti-roll bars.
- **Tires by a magic formula**, with slip, slip angle and a friction ellipse; traction control and ABS.
- **Engine** with a torque curve, a clutch that slips pulling away, and a limiter.
- **Gearbox**, automatic or manual, and an open, locked or limited-slip **differential**.
- **Per kind**: tracks that turn on the spot (tank); a motorcycle that leans into its turns by itself; buoyancy, a propeller and a rudder (boat); wings with stall and control surfaces (airplane); a rotor with collective, cyclic and stability that hovers when let go (helicopter).

Player controls:

| Vehicle | Controls |
|---|---|
| Car, motorcycle, truck, tank | **W/S** throttle; S brakes, then backs up. **A/D** steer. **Space** handbrake. **F/G/H/J** open the parts (doors, hood, bed). |
| Airplane and helicopter | **W/S** pitch. **A/D** roll. **Q/E** yaw. **Shift/Ctrl** throttle (airplane) or collective (helicopter). |

```blueprint
Event BeginPlay -> Enter Vehicle ( Target )
```
```real
class Driver extends Actor
    event Tick(dt: float)
        SetThrottleInput(1)
        SetSteeringInput(0.3)
```
Other nodes: *Set Brake Input*, *Set Handbrake Input*, *Set Flight Input*, *Set Gear*, *Set Engine On*, *Set Part Position*, *Toggle Part*, *Exit Vehicle*, *Get Engine RPM*, *Get Current Gear*. See also [Vehicle parts](article:vehicle-parts) and [Water and rails](article:water-rails).
