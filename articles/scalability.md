id: scalability
kind: howto
title: Escalabilidade e qualidade gráfica | Scalability and graphics quality
keys: vrs, variable rate shading, sombreamento de taxa variavel, gtao, ssao, oclusao de ambiente, ambient occlusion, cantos escuros, escalabilidade, qualidade grafica, baixo medio alto epico, low medium high epic, presets, configuracoes graficas, pc fraco, notebook, msaa, anti aliasing, modo desempenho, modo qualidade, mapa de sombra, shadow map, sem ray tracing, gpu sem rt, luz atravessa parede
--- pt
- **Configurações** (canto superior direito do editor): Baixo, Médio, Alto, Épico. [Mostrar onde](show:Settings)
- Cada recurso caro tem preset: sombras, GI, nuvens, neblina volumétrica, MSAA/TSR.
- **Sombras das luzes locais** (pontuais, spot, retangulares): traçadas por raio do **Médio** para cima. No **Baixo**, e numa GPU sem ray tracing em qualquer preset, vêm de **mapas de sombra**: as luzes mais importantes na tela (tamanho, distância, intensidade) ganham um mapa, as outras ficam sem sombra.
  - Quantas luzes com mapa: Baixo 8, Médio 16, Alto 24, Épico 32. A resolução de cada uma segue o tamanho dela na tela.
  - Os mapas ficam guardados: só se redesenha o que mudou (a luz se moveu, um objeto se moveu dentro do alcance dela).
  - Uma luz só projeta sombra com **Cast Shadows** ligado (Details da luz). Desligar em luzes pequenas e de enfeite poupa o orçamento.
- **Oclusão de ambiente em tela (GTAO)**, do **Alto** para cima: os cantos (parede com chão, com teto, móveis encostados) ganham a sombra suave da luz indireta. Custa ~0,3 ms a 1440p.
- **Variable Rate Shading** (Configurações do Projeto > Rendering, desligado por padrão): sombreia as áreas lisas a cada 2×2 pixels, ~0,4 ms a menos a 1440p, com um pouco mais de cintilação em bordas finas.
- O jogo empacotado tem a sua em Configurações do Projeto > Rendering, e o projeto pode ser **Desempenho** ou **Qualidade** (o path tracer como vista do jogo).
--- en
- **Settings** (the editor's top right): Low, Medium, High, Epic. [Show me where](show:Settings)
- Each costly feature has presets: shadows, GI, clouds, volumetric fog, MSAA/TSR.
- **Local lights' shadows** (point, spot, rect): ray traced from **Medium** up. On **Low**, and on a GPU without ray tracing at any preset, they come from **shadow maps**: the lights that matter most on screen (size, distance, intensity) get a map, the others cast none.
  - How many lights get a map: Low 8, Medium 16, High 24, Epic 32. Each one's resolution follows its size on screen.
  - The maps are kept: only what changed is drawn again (the light moved, an object moved inside its reach).
  - A light casts shadows only with **Cast Shadows** on (the light's Details). Turning it off on small decorative lights saves the budget.
- **Screen space ambient occlusion (GTAO)**, from **High** up: corners (wall and floor, wall and ceiling, furniture against a wall) get the soft shadow of the indirect light. It costs ~0.3 ms at 1440p.
- **Variable Rate Shading** (Project Settings > Rendering, off by default): shades flat areas once per 2×2 pixels, ~0.4 ms less at 1440p, with a little more shimmer on thin edges.
- The packaged game has its own in Project Settings > Rendering, and the project can be **Performance** or **Quality** (the path tracer as the game's view).
