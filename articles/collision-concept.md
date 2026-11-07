id: collision-concept
kind: concept
title: Colisão e sobreposição | Collision and overlap
keys: colisao, colidir, atravessar parede, passa por dentro, overlap, sobreposicao, trigger, gatilho, bloquear, collision, nao colide
--- pt
```diagram compare
 | Colisão | Sobreposição
Bloqueia | sim | não
Eventos BeginOverlap | não | sim
Exemplo | parede, chão | moeda, zona, porta automática
```
- **Colisão**: o ator bloqueia (o personagem não atravessa).
- **Sobreposição (overlap)**: o ator deixa passar, mas avisa: os eventos **BeginOverlap / EndOverlap** rodam.
- Um **Trigger** (Ator > Adicionar) é uma caixa invisível só de sobreposição. [Adicionar um Trigger](add:Trigger)
- As peças de protótipo (Caixa, Escada, Rampa...) já colidem.
- O personagem atravessa algo? Confira a colisão no Details do ator.
--- en
```diagram compare
 | Collision | Overlap
Blocks | yes | no
BeginOverlap events | no | yes
Example | wall, floor | coin, zone, automatic door
```
- **Collision**: the actor blocks (the character doesn't pass through).
- **Overlap**: the actor lets things through, but tells: the **BeginOverlap / EndOverlap** events run.
- A **Trigger** (Actor > Add) is an invisible overlap-only box. [Add a Trigger](add:Trigger)
- The prototyping pieces (Box, Stairs, Ramp...) collide already.
- The character goes through something? Check the actor's collision in Details.
