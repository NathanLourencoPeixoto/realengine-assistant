id: character-physics
kind: concept
title: Personagem e física: degraus, caixas, plataformas | Character and physics: steps, boxes, platforms
keys: plataforma que gira, rotating platform, carrossel, merry go round, girar com a plataforma, turn with platform, ator criado colide, spawned actor collision, spawn actor bloqueia, personagem empurrar caixa, empurrar objeto andando, character push, push box, subir degrau, step up, escada, degrau, plataforma movel, moving platform, elevador, elevator, ficar em cima da caixa, stand on box, personagem atravessa, character goes through, sem colisao, no collision, collision enabled, colisao ligada
--- pt
O **Character** (Character Movement) já faz, sem nó nenhum:
- **Sobe degraus** de até 45 cm andando (escadas, meio-fios, caixas baixas).
- **Empurra** atores com **Simular Física** ao andar contra eles: um corpo de até 80 kg vai na velocidade do personagem; um mais pesado, menos.
- **Fica em cima** de corpos e atores **Movable** que se movem e **vai junto** (plataformas, elevadores, barcos feitos de caixas): mova a plataforma por Blueprint (Set Actor Location, Add Actor World Offset, Timeline) ou pelo Sequencer.
- Uma plataforma que **gira** (yaw) gira quem está em cima em volta do centro dela, e a câmera junto (a rotação de controle), como na Unreal.
- Atores criados no Play (**Spawn Actor**, um Pickup largado) **bloqueiam** a partir do quadro seguinte; destruídos deixam de bloquear. Nada é refeito no nível: o custo é o do ator novo.
- Um ator que não deve bloquear: **Details > Static Mesh > Colisão Ligada** desligada (o NoCollision da Unreal).

```diagram steps
Plataforma Movable | Blueprint move a plataforma | o Character em cima vai junto | anda contra uma caixa com física | a caixa é empurrada
```
--- en
The **Character** (Character Movement) already does, with no node:
- **Steps up** to 45 cm while walking (stairs, curbs, low boxes).
- **Pushes** actors with **Simulate Physics** by walking into them: a body up to 80 kg goes at the character's speed; a heavier one, slower.
- **Stands on** bodies and **Movable** actors that move and **goes along** (platforms, elevators, boats made of boxes): move the platform by Blueprint (Set Actor Location, Add Actor World Offset, Timeline) or with the Sequencer.
- A **turning** platform (yaw) turns whoever stands on it around its center, and the camera with it (the control rotation), as in Unreal.
- Actors made while playing (**Spawn Actor**, a dropped Pickup) **block** from the next frame; destroyed ones stop blocking. Nothing of the level is made again: the cost is the new actor's.
- An actor that shouldn't block: **Details > Static Mesh > Collision Enabled** off (Unreal's NoCollision).

```diagram steps
Movable platform | a Blueprint moves the platform | the Character on it goes along | walks into a box with physics | the box is pushed
```
