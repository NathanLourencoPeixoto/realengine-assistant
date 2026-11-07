id: ecs-architecture
kind: concept
title: Arquitetura: ECS e dados (programar a engine) | Architecture: ECS and data (programming the engine)
keys: ecs, arquitetura, data oriented, orientado a dados, arquetipo, soa, entidade, componente, sistema, job system, memoria, alocacao, engine source, codigo da engine
--- pt
```diagram compare
 | Objetos (herança) | ECS (dados)
Dados | espalhados | contínuos (SoA)
Cache da CPU | muitas faltas | sequencial
Milhões de atores | difícil | sim
Paralelo | travas | por estágio, sem travas
```
- **ECS por arquétipos:** a entidade é um índice + geração; os componentes ficam em arrays contínuos (SoA) por arquétipo; sistemas são funções que percorrem os arrays.
- **Sem malloc no quadro:** alocadores lineares por quadro e pools, alinhados a 64 bytes.
- **Job system:** workers fixos, um por núcleo; sistemas em estágios pelas dependências de leitura e escrita.
- **Render GPU-driven:** culling e LOD na GPU, bindless, poucos draws indiretos, quadros em voo com timeline semaphore.
- **PIE** copia os arrays do mundo (memcpy) ao entrar e restaura ao sair.
--- en
```diagram compare
 | Objects (inheritance) | ECS (data)
Data | scattered | contiguous (SoA)
CPU cache | many misses | sequential
Millions of actors | hard | yes
Parallel | locks | per stage, lock-free
```
- **Archetype ECS:** an entity is an index + generation; components sit in contiguous arrays (SoA) per archetype; systems are functions walking the arrays.
- **No malloc in a frame:** linear per-frame allocators and pools, 64-byte aligned.
- **Job system:** fixed workers, one per core; systems in stages by their read and write dependencies.
- **GPU-driven rendering:** culling and LOD on the GPU, bindless, few indirect draws, frames in flight with a timeline semaphore.
- **PIE** copies the world's arrays (memcpy) on entering and restores them on leaving.
