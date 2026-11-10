id: collision-shapes
kind: howto
title: Formas de colisão: caixa, esfera, cápsula, convexo, malha complexa | Collision shapes: box, sphere, capsule, convex, complex mesh
keys: forma de colisao, collision shape, colisao convexa, convex hull, casco convexo, capsula, capsule, cilindro rola, cylinder, cone, malha complexa, use complex collision, usar malha complexa, escada, stairs, rampa, ramp, atravessa o chao, cai de lado, colide como caixa, gjk, epa, simple collision, complex collision, triangulos, triangles
--- pt
Cada ator com **Física** colide com uma forma, escolhida em **Details > Física > Forma de Colisão** (como a colisão simples da Unreal):
- **Automática** (padrão): o cubo vira caixa, a esfera vira esfera, o cilindro vira um **cilindro de verdade** (rola e fica de pé), o cone e as **malhas importadas** viram o **casco convexo** da malha (até 64 vértices, feito na primeira vez e guardado).
- **Caixa**, **Esfera**, **Cápsula** (no eixo mais comprido da malha, larga como os outros dois) ou **Convexo** (o casco de qualquer malha).
- Para o **cenário** (um ator que não simula): marque **Usar Malha Complexa** e os próprios triângulos da malha colidem: escadas, rampas, arcos, qualquer forma côncava. Só para o que fica parado; o que se move usa a forma simples.

```diagram compare
 | Caixa | Esfera / Cápsula | Convexo | Malha Complexa
Custo | o menor | baixo | médio | por triângulo
Rola | não | sim | conforme a forma | não se move
Côncavo (escada, arco) | não | não | não | sim
Para | caixotes, paredes | bolas, personagens | pedras, garrafas, móveis | cenário parado
```
```diagram steps
Selecionar o ator | Details > Adicionar > Física | Forma de Colisão: Automática, Caixa, Esfera, Cápsula ou Convexo | Cenário: desligar Simular Física e marcar Usar Malha Complexa | Play (Alt+P)
```
- Um objeto atravessa a escada ou fica "flutuando" numa rampa? A escada está com a forma simples (o casco convexo dela é uma rampa): marque **Usar Malha Complexa**.
- O Debug Viewer (F10) mostra o custo da física; o GJK e o EPA (a detecção entre formas) aparecem na medida do teste.
--- en
Each actor with **Physics** collides with a shape, chosen in **Details > Physics > Collision Shape** (like Unreal's simple collision):
- **Automatic** (default): the cube is a box, the sphere a sphere, the cylinder a **real cylinder** (it rolls and stands up), the cone and **imported meshes** the mesh's **convex hull** (up to 64 vertices, made the first time and kept).
- **Box**, **Sphere**, **Capsule** (along the mesh's longest axis, as wide as the other two) or **Convex Hull** (the hull of any mesh).
- For the **scenery** (an actor that doesn't simulate): check **Use Complex Collision** and the mesh's own triangles collide: stairs, ramps, arches, any concave shape. Only for what stays still; what moves uses its simple shape.

```diagram compare
 | Box | Sphere / Capsule | Convex Hull | Complex Mesh
Cost | lowest | low | medium | per triangle
Rolls | no | yes | as its shape | doesn't move
Concave (stairs, arch) | no | no | no | yes
For | crates, walls | balls, characters | rocks, bottles, furniture | still scenery
```
```diagram steps
Select the actor | Details > Add > Physics | Collision Shape: Automatic, Box, Sphere, Capsule or Convex Hull | Scenery: turn off Simulate Physics and check Use Complex Collision | Play (Alt+P)
```
- Something goes through the stairs or "floats" on a ramp? The stairs have their simple shape (their convex hull is a ramp): check **Use Complex Collision**.
- The Debug Viewer (F10) shows the physics' cost; GJK and EPA (the shapes' detection) appear in the test's measure.
