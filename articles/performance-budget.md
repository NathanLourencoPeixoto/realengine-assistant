id: performance-budget
kind: concept
title: Orçamento de desempenho (para profissionais) | Performance budget (for professionals)
keys: orcamento, budget, 200 fps, 100 fps, 10 ms, meta de fps, profiling, perfilar, gargalo, cpu bound, gpu bound, timestamps, medir custo, otimizacao profissional, fatias do quadro, frame budget, orcamento do quadro, frame slices
--- pt
```diagram bars ms
Geometria e materiais: 3.0
Luz direta e sombras: 1.5
GI e reflexos: 3.0
Volumes, água e céu: 1.0
Câmera, cor e pós: 0.8
Reconstrução e UI: 0.7
```
- As metas da engine: **200 FPS a 1440p** na GPU de desenvolvimento (5 ms por quadro) nas cenas simples e abaixo do Épico; no **Épico**, o vídeo-realismo cabe em **10 ms** (acima de 100 FPS). O gráfico mostra como os 10 ms se dividem.
- **F10 Debug Viewer > Frame Budget:** cada fatia do quadro com o tempo de agora e a meta dela; o que passou aparece como "(over)". As fatias de CPU também estão lá: render, Blueprints, física, animação, IA, partículas e os módulos de jogo. [Abrir](open:debug)
- **Medir antes de mudar:** a barra de status separa CPU e GPU; **Ferramentas > Medir o Quadro (3 s)** dá médias estáveis. [Medir](run:measure)
- **Na linha de comando:** `--bench 5 --budget 10` mede 5 s e falha se a GPU ou a CPU passar de 10 ms; com `--budget-strict`, falha também quando uma fatia passa da meta dela. Os testes `budget_house`, `budget_rpg` e `budget_heavy` usam isso.
- **Modo de visualização Object Cost:** colore cada objeto pelo custo.
- CPU alta: lógica por Tick demais (use timers, eventos), muitos atores com IA, animação de muitos personagens.
- GPU alta: resolução e escalabilidade (TSR ou upscaler), sombras, materiais translúcidos, luzes locais sobrepostas, malhas sem LOD.
--- en
```diagram bars ms
Geometry and materials: 3.0
Direct light and shadows: 1.5
GI and reflections: 3.0
Volumes, water and sky: 1.0
Camera, color and post: 0.8
Reconstruction and UI: 0.7
```
- The engine's targets: **200 FPS at 1440p** on the development GPU (5 ms a frame) in simple scenes and below Epic; at **Epic**, video realism fits **10 ms** (above 100 FPS). The chart shows how the 10 ms are split.
- **F10 Debug Viewer > Frame Budget:** each slice of the frame with its time now and its goal; one past it shows "(over)". The CPU slices are there too: render, Blueprints, physics, animation, AI, particles and the game modules. [Open it](open:debug)
- **Measure before changing:** the status bar splits CPU and GPU; **Tools > Measure Frame Time (3 s)** gives steady averages. [Measure](run:measure)
- **From the command line:** `--bench 5 --budget 10` measures 5 s and fails when the GPU or the CPU goes past 10 ms; with `--budget-strict` it also fails when a slice goes past its goal. The tests `budget_house`, `budget_rpg` and `budget_heavy` use it.
- **The Object Cost view mode:** colors each object by its cost.
- High CPU: too much logic per Tick (use timers, events), many actors with AI, many animated characters.
- High GPU: resolution and scalability (TSR or an upscaler), shadows, translucent materials, overlapping local lights, meshes without LODs.
