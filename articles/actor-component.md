id: actor-component
kind: concept
title: O que é um ator e um componente | What an actor and a component are
keys: ator, atores, actor, actors, componente, component, o que e ator, objeto do jogo, entidade, game object
--- pt
- Um **ator** é qualquer coisa que está no nível: um cubo, uma luz, o personagem, uma câmera, um som.
- Um ator é feito de **componentes**: a malha (o que se vê), a colisão, a luz, o som, o movimento...
- Em Blueprints você monta os componentes na aba Viewport da classe; no editor, o painel **Details** mostra os de cada ator.
- Por baixo, a Real Engine guarda os atores como dados contínuos (ECS): é por isso que aguenta milhões deles. [Para quem programa a engine](article:ecs-architecture)
--- en
- An **actor** is anything in the level: a cube, a light, the character, a camera, a sound.
- An actor is made of **components**: the mesh (what you see), the collision, the light, the sound, the movement...
- In Blueprints you set the components up in the class's Viewport tab; in the editor, the **Details** panel shows each actor's.
- Underneath, the Real Engine keeps actors as contiguous data (ECS): that's why it handles millions of them. [For engine programmers](article:ecs-architecture)
