id: performance-budget
kind: concept
title: Orçamento de desempenho (para profissionais) | Performance budget (for professionals)
keys: orcamento, budget, 200 fps, meta de fps, profiling, perfilar, gargalo, cpu bound, gpu bound, timestamps, medir custo, otimizacao profissional
--- pt
```diagram bars ms
Sombras (exemplo): 0.6
GI: 1.2
Passe principal: 1.8
Pós e TSR: 0.6
Interface: 0.3
```
- A meta da engine: **200 FPS a 1440p** na GPU de desenvolvimento (5 ms por quadro), com cenas pesadas tendo metas próprias.
- **Medir antes de mudar:** a barra de status separa CPU e GPU; **Ferramentas > Medir o Quadro (3 s)** dá médias estáveis. [Medir](run:measure)
- **F10 Debug Viewer:** o custo por sistema e por objeto (medido só com ele aberto). [Abrir](open:debug)
- **Modo de visualização Object Cost:** colore cada objeto pelo custo.
- CPU alta: lógica por Tick demais (use timers, eventos), muitos atores com IA, animação de muitos personagens.
- GPU alta: resolução e escalabilidade, sombras, materiais translúcidos, luzes locais sobrepostas, malhas sem LOD.
--- en
```diagram bars ms
Shadows (example): 0.6
GI: 1.2
Main pass: 1.8
Post and TSR: 0.6
UI: 0.3
```
- The engine's target: **200 FPS at 1440p** on the development GPU (5 ms a frame), with heavy scenes having their own targets.
- **Measure before changing:** the status bar splits CPU and GPU; **Tools > Measure Frame Time (3 s)** gives steady averages. [Measure](run:measure)
- **F10 Debug Viewer:** the cost per system and per object (measured only while it's open). [Open it](open:debug)
- **The Object Cost view mode:** colors each object by its cost.
- High CPU: too much logic per Tick (use timers, events), many actors with AI, many animated characters.
- High GPU: resolution and scalability, shadows, translucent materials, overlapping local lights, meshes without LODs.
