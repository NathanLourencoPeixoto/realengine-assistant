id: vehicle-from-mesh
kind: recipe
title: Veículo a partir do seu modelo importado | A vehicle from your imported model
keys: veiculo da minha malha, vehicle from mesh, carro importado, imported car, meu modelo, my model, criar veiculo, make vehicle, malha importada, imported mesh, rodas, wheels, carroceria, body, roda nao gira, wheel not spinning, fbx carro, gltf carro, car model, modelo de carro, transformar em veiculo, turn into vehicle, converter em carro
--- pt
```diagram steps
Importe o modelo (FBX, glTF, OBJ, .tlend) e arraste para o nível | Selecione as peças: carroceria, rodas e portas | Ator > Criar Veículo a partir da Seleção > Carro (ou outro tipo) | Play (Alt+P): já dirige (W/S, A/D, Espaço)
```
## Como funciona
Você não precisa montar nada à mão. Selecione no nível as peças do seu modelo e use **Ator > Criar Veículo a partir da Seleção** (ou o botão **Criar Veículo...** nos Detalhes de uma malha):
- A peça **maior** vira a **carroceria** (a caixa de colisão e o centro de massa saem do tamanho dela).
- As **rodas** são achadas pelo nome (*wheel, tire, roda, pneu, rueda...*) ou, sem nome, pelo formato (redondas, embaixo). O raio, a largura e o lugar de cada uma são medidos; a suspensão, o pneu, a direção e a tração vêm do modelo do tipo escolhido (dianteiras viram, traseiras puxam).
- **Portas** (*door, porta, puerta*) giram pela borda da frente (F abre). O resto acompanha a carroceria.
- Modelo de uma peça só (rodas dentro da carroceria)? As rodas são postas embaixo dos cantos, invisíveis: o carro anda igual.

O veículo novo fica com **Possuir Automaticamente** ligado: aperte Play e dirija. O asset vai para `Content/Vehicles`; com duplo clique você ajusta **Seu Modelo** (malha da carroceria, deslocamento, giro, **Ajustar à Malha da Carroceria**) e a **Malha** de cada peça.

Se o carro andar de lado, a frente do modelo não é +X: em **Ator > Criar Veículo a partir da Seleção > Frente** escolha +X, -X, +Y ou -Y e crie de novo (ou mude o **Giro da Carroceria** no asset).
```blueprint
Event BeginPlay -> Enter Vehicle ( MyCar )
```
Veja também [Veículos](article:vehicles) e [Peças do veículo](article:vehicle-parts).
--- en
```diagram steps
Import the model (FBX, glTF, OBJ, .tlend) and drag it into the level | Select its pieces: body, wheels and doors | Actor > Make Vehicle from Selected > Car (or another kind) | Play (Alt+P): it drives at once (W/S, A/D, Space)
```
## How it works
Nothing to build by hand. Select your model's pieces in the level and use **Actor > Make Vehicle from Selected** (or the **Make Vehicle...** button in a mesh's Details):
- The **biggest** piece becomes the **body** (the collision box and the center of mass come from its size).
- The **wheels** are found by their names (*wheel, tire, roda, pneu, rueda...*) or, unnamed, by their shape (round, low). Each one's radius, width and place are measured; the suspension, tire, steering and drive come from the chosen kind's template (front wheels steer, rear wheels pull).
- **Doors** (*door, porta, puerta*) swing on their front edge (F opens). Everything else rides on the body.
- A model in one piece (wheels inside the body)? The wheels are put under the corners, invisible: the car drives the same.

The new vehicle has **Auto Possess** on: press Play and drive. Its asset goes to `Content/Vehicles`; double-click it to adjust **Your Model** (body mesh, offset, turn, **Fit to Body Mesh**) and each part's **Mesh**.

If the car drives sideways, the model's front isn't +X: in **Actor > Make Vehicle from Selected > Front** pick +X, -X, +Y or -Y and make it again (or change the asset's **Body Turn**).
```blueprint
Event BeginPlay -> Enter Vehicle ( MyCar )
```
See also [Vehicles](article:vehicles) and [Vehicle parts](article:vehicle-parts).
