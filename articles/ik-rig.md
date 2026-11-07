id: ik-rig
kind: recipe
title: IK Rig: mãos, pés e cabeça alcançando alvos | IK Rig: hands, feet and heads reaching targets
keys: ik, ik rig, cinematica inversa, inverse kinematics, fabrik, full body ik, corpo inteiro, chain ik, cadeia, limb ik, two bone ik, look at, olhar para, mao na parede, hand on wall, pe no degrau, foot on step, alvo, goal, meta, target, tentaculo, tentacle, cauda, tail, monstro, monster, pescoco, neck, set ik goal, clear ik goal, pole vector, rigidez, stiffness, limite, limit
--- pt
```diagram steps
Content Browser > Adicionar > IK Rig e Física > IK Rig para: (o Skeletal Mesh) | Metas (Goals) nos ossos: mãos, pés, cabeça | Solvers em ordem: Chain, Limb, Full Body, Look At | Detalhes do Skeletal Mesh > IK Rig | Set IK Goal no Blueprint (ou a meta segue um ator)
```
## Como funciona
Um **IK Rig** (`.rikrig`, como o da Unreal) move os ossos depois da animação para que um osso **alcance uma meta**:
- **Metas (Goals)**: um osso (a mão, o pé, a cabeça, a ponta de um tentáculo) e para onde ele vai. A meta segue um **ator do nível** pelo nome (com um deslocamento) ou é posta pelo Blueprint com **Set IK Goal**.
- **Solvers**, rodando em ordem:
  - **Chain IK**: uma cadeia de **qualquer número de ossos** (FABRIK): caudas, tentáculos, pescoços longos, braços de monstros. *Pole Vector* escolhe para que lado a cadeia dobra.
  - **Limb IK**: dois ossos (braço, perna) com o seu pole.
  - **Full Body IK**: várias metas a partir de uma raiz (a bacia). A raiz também anda, conforme a *Root Stiffness*: as mãos alcançam algo longe e o corpo se inclina junto.
  - **Look At**: um osso apontado para a meta (a cabeça olhando).
- **Configurações por osso**: *Stiffness* (o quanto o osso mantém a pose animada) e *Limit* (o cone, em graus, que ele pode girar): sem cotovelos ao contrário.

Ao criar, o IK Rig acha sozinho as mãos, os pés e a cabeça pelos nomes e já monta um Full Body e um Look At. No editor, **arraste uma meta** na prévia e veja os solvers alcançarem na hora.

```blueprint
Event Tick -> Set IK Goal ( Goal, Location, Alpha )
```
```real
class Climber extends Actor
    event Tick(dt: float)
        SetIKGoal("RightHand", GetActorLocation() + Vector(40, 30, 120), 1)
```
*Clear IK Goal* solta a meta (sem nome: todas) e os ossos voltam à animação. Veja também [Ragdoll e Physics Asset](article:ragdoll).
--- en
```diagram steps
Content Browser > Add > IK Rig and Physics > IK Rig for: (the Skeletal Mesh) | Goals on bones: hands, feet, head | Solvers in order: Chain, Limb, Full Body, Look At | Skeletal Mesh Details > IK Rig | Set IK Goal in a Blueprint (or the goal follows an actor)
```
## How it works
An **IK Rig** (`.rikrig`, like Unreal's) moves the bones after the animation so a bone **reaches a goal**:
- **Goals**: a bone (the hand, the foot, the head, a tentacle's tip) and where it goes. A goal follows a **level actor** by name (with an offset) or is set by Blueprint with **Set IK Goal**.
- **Solvers**, run in order:
  - **Chain IK**: a chain of **any number of bones** (FABRIK): tails, tentacles, long necks, monster arms. *Pole Vector* picks which way the chain bends.
  - **Limb IK**: two bones (an arm, a leg) with its pole.
  - **Full Body IK**: several goals from one root (the pelvis). The root moves too, by its *Root Stiffness*: the hands reach something far and the body leans with them.
  - **Look At**: a bone aimed at its goal (the head looking).
- **Bone settings**: *Stiffness* (how much the bone keeps its animated pose) and *Limit* (the cone, in degrees, it may turn): no elbows bending backwards.

When made, the IK Rig finds the hands, feet and head by their names and sets up a Full Body and a Look At. In the editor, **drag a goal** in the preview and watch the solvers reach it live.

```blueprint
Event Tick -> Set IK Goal ( Goal, Location, Alpha )
```
```real
class Climber extends Actor
    event Tick(dt: float)
        SetIKGoal("RightHand", GetActorLocation() + Vector(40, 30, 120), 1)
```
*Clear IK Goal* releases the goal (no name: all of them) and the bones go back to the animation. See also [Ragdoll and Physics Asset](article:ragdoll).
