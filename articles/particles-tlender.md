id: particles-tlender
kind: howto
title: Partículas do Tlender numa malha | Tlender particles on a mesh
keys: particulas tlender, tlender particles, blender particles, particulas do blender, emitir da malha, emit from faces, emit from verts, volume, halo, render as object, instanciar objeto, particle properties, numero de particulas, frame start, lifetime, newtonian, gravidade, cabelo, hair, chuva de objetos
--- pt
```diagram steps
Selecione um ator com malha | Detalhes > Adicionar > Partículas (Tlender) | Número, quadros, vida, emitir de faces/vértices/volume | Halo (brilho ou iluminado) ou Objeto (uma malha)
```
## O que é
O mesmo sistema de partículas do **Tlender** (o do Blender): um número de partículas nasce entre o **Quadro Inicial** e o **Fim**, a partir das **faces**, dos **vértices** ou do **volume** da malha do ator, com velocidade ao longo da **Normal**, aleatória e do objeto; física **Newtoniana** (gravidade, arrasto, browniano).
- **Renderizar Como Halo**: sprites que brilham (Brilho em nits) ou iluminados pelo sol e o céu.
- **Renderizar Como Objeto**: uma malha em cada partícula (Objeto Instanciado), com sombra.
- **Repetir** faz nascer de novo depois do fim. Em **Espaço Local** as partículas andam com o ator.
Roda na mesma simulação da GPU dos Sistemas de Partículas: milhões, em tempo real.
--- en
```diagram steps
Select an actor with a mesh | Details > Add > Particles (Tlender) | Number, frames, life, emit from faces/verts/volume | Halo (glowing or lit) or Object (a mesh)
```
## What it is
The **Tlender's** particle system (Blender's): a number of particles are born between **Frame Start** and **End**, from the **faces**, **vertices** or **volume** of the actor's mesh, with velocity along the **Normal**, at random and of the object; **Newtonian** physics (gravity, drag, brownian).
- **Render As Halo**: sprites that glow (Glow in nits) or lit by the sun and the sky.
- **Render As Object**: a mesh at each particle (Instance Object), shadowed.
- **Loop** makes them born again after the end. In **Local Space** the particles move with the actor.
It runs on the same GPU simulation as the Particle Systems: millions, in real time.
