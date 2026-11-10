id: test-suite
kind: concept
title: Suíte de testes da engine e o kit rápido (para profissionais) | The engine's test suite and the quick kit (for professionals)
keys: testes, suite, suíte, ctest, kit rapido, quick kit, regressao, regression, areas, etiquetas, labels, tools/suite.ps1, testar a engine, run tests
--- pt
```diagram steps
Cada teste tem a etiqueta da sua área | O kit: o teste mais barato de cada área | Com janela: um por vez na GPU | Sem janela: ao lado
```
- Para quem compila a Real Engine a partir do código: a suíte (`ctest`, ~200 testes) leva ~20 min; o **kit rápido** passa por todas as 51 áreas em ~4 min.
- `tools/suite.ps1` roda o kit; `-Areas fisica,ia` soma as áreas inteiras que você mexeu; `-Completa` roda tudo (antes de uma build); `-Falhas` repete só o que falhou; `-Listar` mostra cada área e o que está no kit.
- Tudo roda escondido, sem roubar a tela. Feche o editor instalado antes: a GPU dividida baixa o fps e os testes falham por tempo, não por erro.
- Teste novo: entra na linha da sua área em `tools/suite_areas.cmake`; o teste `suite_areas` acusa um teste sem área ou uma área sem teste no kit.
- Veja também: [Orçamento do quadro](article:performance-budget), [Debug Viewer](article:debug-viewer).
--- en
```diagram steps
Each test has its area's label | The kit: each area's cheapest test | With a window: one at a time on the GPU | Without one: alongside
```
- For those who build the Real Engine from source: the suite (`ctest`, ~200 tests) takes ~20 min; the **quick kit** goes through all 51 areas in ~4 min.
- `tools/suite.ps1` runs the kit; `-Areas fisica,ia` adds the whole areas you touched; `-Completa` runs everything (before a build); `-Falhas` repeats only what failed; `-Listar` shows each area and what is in the kit.
- Everything runs hidden, never taking the screen. Close the installed editor first: a shared GPU lowers the fps and tests fail on time, not on a bug.
- A new test: goes on its area's line in `tools/suite_areas.cmake`; the `suite_areas` test flags a test with no area or an area with no test in the kit.
- See also: [Frame budget](article:performance-budget), [Debug Viewer](article:debug-viewer).
