id: cloth
kind: howto
title: Tecido: bandeiras, cortinas, capas e rasgos | Cloth: flags, curtains, capes and tears
keys: tecido, cloth, pano, fabric, roupa, clothing, bandeira, flag, cortina, curtain, capa, cape, vela, sail, lencol, sheet, rasgar, tear, rip, simulacao de tecido, cloth simulation, chaos cloth, nvcloth, vbd, xpbd, vento, wind, seda, silk, algodao, cotton, couro, leather, sombra do tecido, cloth shadow, auto colisao, self collision, dobras, folds, camadas, layers, saia, skirt, vestido, dress, roupa importada, imported garment, malha propria, mesh cloth, criar tecido a partir da selecao, make cloth from selected, faixa presa, pin band
--- pt
```diagram steps
Adicionar Rápido > Tecido > um tipo (Seda, Algodão, Bandeira, Capa...) | Detalhes: Preso, tamanho, rigidez, vento, Rasga ao Esticar | Janela > Simulação de Tecido: todos, custo, rasgar | Blueprint: Tear Cloth (um corte)
```
## Como funciona
Cada ator **Cloth** é um tecido simulado na GPU pelo **Vertex Block Descent** (o estado da arte em tempo real: estável com qualquer rigidez, converge em poucas passadas). Os contatos seguem a ideia do **Offset Geometric Contact**: um vértice nunca anda mais que uma parte da distância até o que vai tocar, então o tecido **não atravessa** nada e mantém a sua **Espessura**.
- Colide com **Skeletal Meshes** (os ossos, com os raios do Physics Asset), **personagens**, **corpos com física** e as **malhas do nível**.
- **Vento** com **Rajada**, **Gravidade**, **Amortecimento**, **Atrito**; tipos prontos (Seda, Algodão, Jeans, Couro, Lona, Bandeira, Capa) ou números próprios.
- **Rasga**: onde um fio estica além de **Rasga ao Esticar**, ou onde um Blueprint corta (**Tear Cloth**).
- **Capa**: **Seguir Ator** + **Seguir Osso** prendem o tecido a um osso de uma Skeletal Mesh.
- **Roupa importada** (saia, vestido, capa, manga): selecione a malha (também uma parte de um personagem importado) e use **Ator > Criar Tecido a partir da Seleção**. O tecido usa a própria malha, soldada nas costuras de UV; a **Faixa Presa** (cm a partir do topo) fica presa e o resto cai, seguindo o osso da parte com o giro inteiro (**Seguir o Giro Inteiro**). No Details, **Malha do Tecido** troca entre grade e uma malha importada. As pernas e o corpo do personagem seguram a roupa.
- **Auto-Colisão**: as dobras e camadas do tecido não se atravessam, nem com os outros tecidos que têm a opção (**Distância da Auto-Colisão**: auto pela espessura e pela resolução). ~0,02 ms por tecido.
- **Projetar Sombra**: o tecido faz sombra do sol (nas sombras virtuais e nas por raio, também encostado no que cobre).
- Vários tecidos juntos: 12 tecidos (34 mil vértices) custam ~0,4 ms numa RTX 3060, mais ~0,35 ms das sombras.
```blueprint
Event Hit -> Tear Cloth ( Hit Location, 25 )
```
--- en
```diagram steps
Quick Add > Cloth > a preset (Silk, Cotton, Flag, Cape...) | Details: Pinned, size, stiffness, wind, Tear Strain | Window > Cloth Simulation: all of them, the cost, tearing | Blueprint: Tear Cloth (a cut)
```
## How it works
Each **Cloth** actor is a sheet simulated on the GPU by **Vertex Block Descent** (the real-time state of the art: stable at any stiffness, converging in a few passes). Contacts follow **Offset Geometric Contact**: a vertex never moves more than a share of its distance to what it will touch, so the cloth **never passes through** anything and keeps its **Thickness**.
- It collides with **Skeletal Meshes** (their bones, with the Physics Asset's radii), **characters**, **physics bodies** and the **level's meshes**.
- **Wind** with **Gust**, **Gravity**, **Damping**, **Friction**; ready presets (Silk, Cotton, Denim, Leather, Canvas, Flag, Cape) or your own numbers.
- **Tears**: where a thread stretches past **Tear Strain**, or where a Blueprint cuts it (**Tear Cloth**).
- **Cape**: **Follow Actor** + **Follow Bone** pin the cloth to a Skeletal Mesh's bone.
- **Imported garment** (skirt, dress, cape, sleeve): select the mesh (a part of an imported character too) and use **Actor > Make Cloth from Selected**. The cloth uses the mesh itself, welded at its UV seams; its **Pin Band** (cm from the top) stays pinned and the rest falls, following the part's bone with its whole turn (**Follow Whole Turn**). In Details, **Cloth Mesh** switches between a grid and an imported mesh. The character's legs and body hold the garment.
- **Self Collision**: the cloth's folds and layers don't pass through one another, nor through the other cloths that have it (**Self Collision Distance**: auto from its thickness and resolution). ~0.02 ms a cloth.
- **Cast Shadow**: the cloth casts the sun's shadow (in the virtual shadow maps and the ray traced ones, also lying on what it covers).
- Many cloths together: 12 cloths (34 thousand vertices) cost ~0.4 ms on an RTX 3060, plus ~0.35 ms for their shadows.
```blueprint
Event Hit -> Tear Cloth ( Hit Location, 25 )
```
