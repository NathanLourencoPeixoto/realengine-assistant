id: async-api
kind: concept
title: Tarefas em segundo plano: a API (estender a engine) | Background tasks: the API (extending the engine)
keys: async, async_run, async_steps, async_track, worker, thread, segundo plano, nao travar o editor, api async, cartoes de progresso
--- pt
Para quem escreve sistemas na engine (C):
- `async_run(label, work, done, arg, flags)`: `work` num worker de baixa prioridade, `done` na thread principal no começo do quadro.
- `async_steps(...)`: fatias na thread principal dentro de um orçamento (6 ms no editor).
- `async_track(...)`: mostra o progresso de algo que já anda sozinho.
- Dentro: `async_status`, `async_progress`, `async_progress_n`, `async_cancelled`, `async_fail`.
- Regra: o worker não toca no mundo, na GPU nem em registros; escreve arquivos ou memória própria. O cartão aparece sozinho (0,15 s).
--- en
For those writing engine systems (C):
- `async_run(label, work, done, arg, flags)`: `work` on a low-priority worker, `done` on the main thread at a frame's start.
- `async_steps(...)`: slices on the main thread within a budget (6 ms in the editor).
- `async_track(...)`: shows the progress of something that runs by itself.
- Inside: `async_status`, `async_progress`, `async_progress_n`, `async_cancelled`, `async_fail`.
- The rule: the worker doesn't touch the world, the GPU or registries; it writes files or its own memory. The card shows by itself (0.15 s).
