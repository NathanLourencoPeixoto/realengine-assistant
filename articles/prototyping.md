id: prototyping
kind: howto
title: Montar fases rápido (peças de protótipo) | Build levels fast (prototyping pieces)
keys: alcas, handles, esticar, portas, mais portas, door, prototipo, blockout, greybox, montar fase rapido, caixa, escada, rampa, parede com porta, sala, corredor, plataforma, level design, array de portas, quantas portas, door array, number of doors
--- pt
- **Ator > Adicionar** tem as peças: **Caixa, Escada, Rampa, Parede (com porta), Sala, Corredor, Plataforma**, ajustadas por números no Details (degraus, largura, altura).
- Já colidem e a navegação da IA anda nelas: dá para testar a fase antes da arte. [Adicionar uma sala](add:Room) [Adicionar uma rampa](add:Ramp)
- **Editar no viewport:** com a peça selecionada, quadradinhos laranja nas faces: arraste para esticar (a face oposta fica parada); o azul na porta a desliza pela parede. **Portas:** Parede e Corredor podem ter de 1 a 8 portas; a Sala pode ter porta também atrás, à esquerda e à direita.
- **Array de portas:** cada parede com porta ganha, logo abaixo da caixa (Porta da Frente, de Trás, Esquerda, Direita), um **array "Portas"** como o da Unreal: **+** adiciona uma porta, a lixeira volta a uma, o **x** de cada elemento remove aquela. Até 8 por parede, distribuídas por igual.

--- en
- **Actor > Add** has the pieces: **Box, Stairs, Ramp, Wall (with a door), Room, Corridor, Platform**, set by numbers in Details (steps, width, height).
- They collide already and the AI's navigation walks on them: you can test the level before the art. [Add a room](add:Room) [Add a ramp](add:Ramp)
- **Edit in the viewport:** with the piece selected, orange squares on its faces: drag to stretch (the opposite face stays); the blue one on the door slides it along the wall. **Doors:** a Wall and a Corridor take 1 to 8 doors; a Room can also have doors at the back, left and right.
- **Door array:** each wall with a door gets, right under its checkbox (Front, Back, Left, Right Door), a **"Doors" array** like Unreal's: **+** adds a door, the bin goes back to one, each element's **x** removes it. Up to 8 a wall, spread evenly.
