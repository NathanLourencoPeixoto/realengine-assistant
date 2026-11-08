id: particle-systems
kind: recipe
title: Sistemas de partículas (como o Niagara) | Particle systems (like Niagara)
keys: particulas, particles, particle system, sistema de particulas, niagara, emissor, emitter, modulo, module, fogo, fire, fumaca, smoke, faisca, sparks, chuva, rain, neve, snow, explosao, explosion, magia, magic, poeira, dust, chafariz, fountain, destrocos, debris, spawn system, sprite, malha de particula, mesh particles, vfx, efeito visual, visual effects, milhoes de particulas, gpu particles
--- pt
```diagram steps
Content Browser > Adicionar > Efeitos Visuais (um modelo) | Duplo clique: emissores e pilha de módulos | "+" em cada estágio (recentes e recomendados no topo) | Arraste para o nível ou Spawn System at Location
```
## Como funciona
Um **Sistema de Partículas** (`.rparticle`) tem **emissores**; cada emissor é uma **pilha de módulos** nos estágios do Niagara:
- **Emitter**: *Spawn Rate* (partículas por segundo) e *Spawn Burst* (de uma vez).
- **Particle Spawn**: *Lifetime*, *Shape Location* (ponto, esfera, caixa, cone, disco ou a malha do ator), *Initial Velocity*, *Size*, *Color*, *Rotation*.
- **Particle Update**: *Gravity*, *Drag*, *Curl Noise*, *Vortex*, *Point Attraction*, *Wind*, *Collision*, *Speed Limit*, *Kill Box*, *Color/Size Over Life*.
- **Render**: *Sprite Renderer* (iluminado como fumaça, ou brilhando e somado como fogo) ou *Mesh Renderer* (uma malha em cada partícula, com sombra do sol).

**O editor (como o do Niagara):** barra com Salvar, Localizar, Tocar/Pausar, Recomeçar e a velocidade; **Prévia** à esquerda (arraste para orbitar, roda para aproximar); **Visão Geral do Sistema** no meio, com um cartão por emissor e os grupos coloridos (Emissor, Nascimento, Atualização, Renderização); **Seleção** à direita com os parâmetros de cada módulo (vetores, cores HDR, listas, caixas); embaixo **Curvas** (Cor e Tamanho ao Longo da Vida, arrastando os pontos) e **Linha do Tempo** (nascimentos e rajadas de cada emissor; arraste para percorrer).

Módulos novos: *Emitter State* (para sempre, uma vez ou N voltas, com atraso; rajada a cada volta), *Sub UV Animation* (flipbook da textura do sprite), *Scale by Speed* (tamanho e opacidade pela velocidade), *Camera Offset* e as formas *cilindro* e *toro*.

Tudo roda na GPU: 5 milhões de partículas a mais de 200 fps em 1440p. Malhas pequenas na tela viram sprites da sua cor, e partículas pequenas viram pontos (1 vértice cada). **Prévia no Nível** mostra cada mudança na hora.

```blueprint
Event BeginPlay -> Spawn System at Location ( Location, Rotation, true )
```
```real
class Torch extends Actor
    event BeginPlay()
        var fx = SpawnSystemAtLocation("PS_Fire", GetActorLocation(), MakeRotator(0, 0, 0), false)
        fx.SetParticleColor(MakeLinearColor(1, 0.4, 0.1, 1))
```
Escolha o sistema nos Detalhes do nó *Spawn System at Location*. *Activate System*, *Deactivate System*, *Set Spawn Rate Scale* e *Is System Active* controlam um sistema já colocado.
Veja também [Partículas do Tlender](article:particles-tlender).
--- en
```diagram steps
Content Browser > Add > Visual Effects (a template) | Double-click: emitters and their module stack | "+" in each stage (recent and recommended on top) | Drag it into the level or Spawn System at Location
```
## How it works
A **Particle System** (`.rparticle`) has **emitters**; each emitter is a **stack of modules** in Niagara's stages:
- **Emitter**: *Spawn Rate* (particles a second) and *Spawn Burst* (all at once).
- **Particle Spawn**: *Lifetime*, *Shape Location* (point, sphere, box, cone, disc or the actor's mesh), *Initial Velocity*, *Size*, *Color*, *Rotation*.
- **Particle Update**: *Gravity*, *Drag*, *Curl Noise*, *Vortex*, *Point Attraction*, *Wind*, *Collision*, *Speed Limit*, *Kill Box*, *Color/Size Over Life*.
- **Render**: *Sprite Renderer* (lit like smoke, or glowing and added like fire) or *Mesh Renderer* (a mesh at each particle, shadowed by the sun).

**The editor (like Niagara's):** a toolbar with Save, Browse, Play/Pause, Restart and the speed; **Preview** on the left (drag to orbit, wheel to zoom); **System Overview** in the middle, a node per emitter with its colored groups (Emitter, Particle Spawn, Particle Update, Render); **Selection** on the right with each module's parameters (vectors, HDR colors, choices, toggles); at the bottom **Curves** (Color and Size Over Life, dragging the points) and **Timeline** (each emitter's spawning and bursts; drag to scrub).

New modules: *Emitter State* (forever, once or N loops, with a delay; a burst each loop), *Sub UV Animation* (a flipbook of the sprite's texture), *Scale by Speed* (size and opacity by speed), *Camera Offset* and the *cylinder* and *torus* shapes.

Everything runs on the GPU: 5 million particles at over 200 fps at 1440p. Meshes small on screen become sprites of their color, and small particles become points (one vertex each). **Preview in Level** shows every change at once.

```blueprint
Event BeginPlay -> Spawn System at Location ( Location, Rotation, true )
```
```real
class Torch extends Actor
    event BeginPlay()
        var fx = SpawnSystemAtLocation("PS_Fire", GetActorLocation(), MakeRotator(0, 0, 0), false)
        fx.SetParticleColor(MakeLinearColor(1, 0.4, 0.1, 1))
```
Pick the system in the Details of the *Spawn System at Location* node. *Activate System*, *Deactivate System*, *Set Spawn Rate Scale* and *Is System Active* control a placed one.
See also [Tlender particles](article:particles-tlender).
