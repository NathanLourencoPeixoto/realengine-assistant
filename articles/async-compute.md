id: async-compute
kind: concept
title: Async compute | Async compute
keys: async compute, compute assincrono, computacao assincrona, fila de compute, compute queue, paralelismo na gpu, gpu parallelism, overlap, sobreposicao, filas da gpu, gpu queues, async shaders
--- pt
```diagram steps
Fila gráfica: o começo do quadro (culling, cena, sombras) é enviado à GPU
Fila de compute, ao mesmo tempo: a simulação das partículas
O resto do quadro (o passe principal) espera só pela simulação, e segue
```
**Async compute** usa a segunda fila da placa (a de compute, que NVIDIA e AMD têm) para rodar um trabalho de compute **ao mesmo tempo** que o gráfico, em vez de um depois do outro.
- **Onde ligar:** Project Settings > Rendering > **Async Compute**. Vem desligado de fábrica, como o Variable Rate Shading.
- **O que vai para a outra fila:** a simulação das partículas. O quadro é enviado em duas partes, e só a segunda, que desenha as partículas, espera por ela.
- **Quando ajuda:** quando o começo do quadro é pesado (muitas sombras, muita cena) e a simulação também. Medido nesta engine (RTX 3060, cena de partículas no Épico), ficou igual ou 0,1 ms mais lento: a simulação é curta demais para compensar o envio extra. Por isso fica opcional.
- Placas sem uma fila só de compute seguem com uma fila, como antes.
--- en
```diagram steps
Graphics queue: the frame's start (culling, scene, shadows) is sent to the GPU
Compute queue, at the same time: the particles' simulation
The rest of the frame (the main pass) waits only for the simulation, then goes on
```
**Async compute** uses the card's second queue (the compute one, which NVIDIA and AMD have) to run compute work **at the same time** as the graphics, instead of one after the other.
- **Where to turn it on:** Project Settings > Rendering > **Async Compute**. It comes off by default, like Variable Rate Shading.
- **What goes to the other queue:** the particles' simulation. The frame is sent in two parts, and only the second, which draws the particles, waits for it.
- **When it helps:** when the frame's start is heavy (many shadows, a lot of scene) and the simulation is too. Measured in this engine (RTX 3060, the particle scene on Epic), it came out the same or 0.1 ms slower: the simulation is too short to pay for the extra submission. That is why it stays optional.
- Cards without a compute-only queue keep a single queue, as before.
