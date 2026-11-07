id: vehicle-parts
kind: concept
title: Peças de veículo: rodas, suspensão, motor, pistões, portas | Vehicle parts: wheels, suspension, engine, pistons, doors
keys: peca de veiculo, vehicle part, roda, wheel, suspensao, suspension, mola, spring, amortecedor, damper, shock, pistao, piston, hidraulico, hydraulic, engrenagem, gear, porta, door, capo, hood, cacamba, dump bed, dobradica, hinge, corredica, slider, helice, propeller, asa, wing, aileron, profundor, elevator, leme, rudder, rotor, boia, pontoon, float, truque, bogie, diferencial, differential, cambio, gearbox, motor, engine, torque
--- pt
```diagram steps
Duplo clique no Veículo | + Peça (o tipo) | Componente: a malha do ator que ela move (pelo nome) | Posição e eixo na vista de cima e de lado | Os números da peça à direita
```
## As peças
Cada peça é física e pode mover um **componente** do ator pelo nome (a malha da roda, o painel da porta).

**Rodas e suspensão**
- **Roda**: raio, mola (N/cm), amortecedor, curso da suspensão, esterço máximo, a parte que recebe do motor (Tração), freio, freio de mão e aderência. A malha gira, esterça e sobe e desce na mola.
- **Pistão**: estica entre o seu ponto e a peça ligada (o amortecedor até o cubo da roda, o macaco da caçamba). Sem ligação, sai pelo eixo conforme a sua entrada.

**Motor e transmissão**
- **Motor**: torque máximo, RPM de pico, máximo e de marcha lenta, e freio motor.
- **Câmbio**: relação final, automático (troca pelas RPM) ou manual. As marchas ficam no chassi.
- **Diferencial**: aberto, travado ou autoblocante.

**Peças móveis**
- **Dobradiça**: portas, capô, caçamba ou canhão giram entre Mín. e Máx. Abrem pela entrada (F/G/H/J) ou pelos nós *Set Part Position* e *Toggle Part*.
- **Corrediça**: porta de correr, braço de guindaste, garfo de empilhadeira.
- **Engrenagem**: gira com outra peça: `Engine` (virabrequim, ventoinha), `Steer` (volante, guidão), uma roda ou outra peça.

**Água e ar**
- **Hélice**: empuxo pelo acelerador; no ar (avião) ou na água (barco).
- **Asa**: sustentação e arrasto pelo ângulo, com estol. Com uma entrada vira **aileron**, **profundor**, **leme** ou **leme de barco** (Na Água).
- **Rotor**: helicóptero, com coletivo, cíclico, torque de cauda e Estabilidade.
- **Boia (Pontoon)**: flutuação e arrasto da água nos pontos do casco.

**Trilhos**
- **Truque (Bogie)**: o truque de um trem, sobre o trilho.

Centro de massa baixo deixa o veículo estável; mola mais dura e amortecedor maior deixam a suspensão firme.
--- en
```diagram steps
Double-click the Vehicle | + Part (its kind) | Component: the actor's mesh it moves (by name) | Its position and axis in the top and side views | Its numbers on the right
```
## The parts
Each part is physics and may move an actor's **component** by name (a wheel's mesh, a door's panel).

**Wheels and suspension**
- **Wheel**: radius, spring (N/cm), damper, suspension travel, max steer, its share of the engine (Drive), brake, handbrake and grip. Its mesh spins, steers and rides its spring.
- **Piston**: stretches between its point and the linked part (a shock to a wheel's hub, a dump bed's ram). Without a link it extends along its axis by its input.

**Engine and drivetrain**
- **Engine**: max torque, peak, max and idle RPM, and engine braking.
- **Gearbox**: final drive, automatic (shifts by RPM) or manual. The gear ratios live on the chassis.
- **Differential**: open, locked or limited slip.

**Moving parts**
- **Hinge**: doors, hood, bed or gun swing between Min and Max. They open by their input (F/G/H/J) or by the *Set Part Position* and *Toggle Part* nodes.
- **Slider**: a sliding door, a crane's arm, a forklift's mast.
- **Gear**: turns with another part: `Engine` (crankshaft, fan), `Steer` (steering wheel, handlebar), a wheel or another part.

**Water and air**
- **Propeller**: thrust by the throttle, in the air (airplane) or in the water (boat).
- **Wing**: lift and drag by its angle, stalling. With an input it becomes an **aileron**, **elevator**, **rudder** or a **boat's rudder** (In Water).
- **Rotor**: a helicopter's, with collective, cyclic, tail torque and Stability.
- **Pontoon**: buoyancy and water drag at the hull's points.

**Rails**
- **Bogie**: a train's truck, on the rail.

A low center of mass keeps the vehicle steady; a stiffer spring and a bigger damper make the suspension firm.
