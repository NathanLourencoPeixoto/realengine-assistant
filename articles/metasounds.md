id: metasounds
kind: howto
title: MetaSounds: som feito por nós (motor, chuva, vento) | MetaSounds: sound made of nodes (engine, rain, wind)
keys: metasound, metasounds, meta sound, som procedural, procedural audio, procedural sound, sintetizador, synth, synthesizer, oscilador, oscillator, ruido, noise, filtro de audio, audio filter, envelope, adsr, som de motor, engine sound, barulho do motor, ronco do motor, rpm sound, som do carro, car sound, som de chuva, rain sound, barulho da chuva, som de vento, wind sound, set float parameter, parametro de som, sound parameter, MS_Engine, MS_Rain, MS_Wind, rmsnd
--- pt
```diagram steps
Content Browser > Adicionar > Sons > MetaSound Source
Nós: Oscilador, Ruído, Impulsos, Filtro, Envelope, contas, Input
Ligue tudo ao Output; Play toca, os Inputs mudam ao vivo
No jogo: Audio Component com o MetaSound + Set Float Parameter
```
Um **MetaSound Source** é um som feito por um grafo de nós de áudio em vez de uma gravação, como o da Unreal: ele muda enquanto toca (a rotação de um motor, a força da chuva) sem trocar de arquivo.
- **Criar:** Content Browser > **Adicionar > Sons > MetaSound Source**. O editor lista os **Inputs** (os parâmetros, com controles que mudam a prévia ao vivo) e os **Nós**; cada entrada de um nó é um valor ou a saída de outro nó.
- **Nós:** **Oscillator** (seno, serra, quadrada, triângulo), **Noise** (branco, rosa, marrom), **Impulses** (cliques aleatórios: gotas, estalos), **Filter** (passa-baixa, passa-alta, passa-banda, com ressonância), **ADSR Envelope**, **Multiply**, **Add**, **Map Range**, **Smooth** (desliza um valor), **Distortion** e **Input** (um parâmetro com nome e valor padrão). Tudo que chega ao **Output** toca.
- **No jogo:** ponha o MetaSound num **Audio Component** (ou em Spawn Sound) e mude os inputs com **Set Float Parameter** (o nome do input e o valor). Ele passa pela mesma atenuação, espacialização, Sound Class e Submix de qualquer som.
- **Prontos** (em `Content/Audio/MetaSounds`): **MS_Engine** (inputs RPM e Load), **MS_Rain** (Intensity em mm/h) e **MS_Wind** (Speed em m/s). A engine já os usa sozinha: cada **veículo** com o motor ligado soa pelo MS_Engine com a sua rotação e o acelerador, e o ator **Rain** toca a chuva e o vento pela intensidade e pelo vento dele. Um Audio Component no próprio ator troca o som automático pelo seu; `REALENGINE_NO_AUTO_SOUNDS` desliga todos.
- **Custo:** o motor (21 nós) gasta ~0,04 ms de CPU a cada 10 ms de som, na thread do mixer, sem alocar memória.
```blueprint
Event Tick -> Set Float Parameter ( Target = EngineAudio, In Name = "RPM", In Float = CurrentRPM )
Event BeginPlay -> Set Float Parameter ( Target = RainAudio, In Name = "Intensity", In Float = 50 )
```
--- en
```diagram steps
Content Browser > Add > Sounds > MetaSound Source
Nodes: Oscillator, Noise, Impulses, Filter, Envelope, math, Input
Wire it all to the Output; Play plays it, the Inputs change it live
In the game: an Audio Component with the MetaSound + Set Float Parameter
```
A **MetaSound Source** is a sound made by a graph of audio nodes instead of a recording, like Unreal's: it changes while it plays (an engine's revs, the rain's strength) without swapping files.
- **Make one:** Content Browser > **Add > Sounds > MetaSound Source**. The editor lists the **Inputs** (the parameters, with controls that change the preview live) and the **Nodes**; each node's input is a value or another node's output.
- **Nodes:** **Oscillator** (sine, saw, square, triangle), **Noise** (white, pink, brown), **Impulses** (random clicks: drops, crackle), **Filter** (low pass, high pass, band pass, with resonance), **ADSR Envelope**, **Multiply**, **Add**, **Map Range**, **Smooth** (glides a value), **Distortion** and **Input** (a parameter with a name and a default). Whatever reaches the **Output** plays.
- **In the game:** put the MetaSound in an **Audio Component** (or in Spawn Sound) and change its inputs with **Set Float Parameter** (the input's name and the value). It goes through the same attenuation, spatialization, Sound Class and Submix as any sound.
- **Ready-made** (in `Content/Audio/MetaSounds`): **MS_Engine** (inputs RPM and Load), **MS_Rain** (Intensity in mm/h) and **MS_Wind** (Speed in m/s). The engine already uses them by itself: every **vehicle** with its engine on sounds through MS_Engine with its revs and throttle, and the **Rain** actor plays the rain and the wind by its intensity and wind. An Audio Component on the actor itself replaces the automatic sound with yours; `REALENGINE_NO_AUTO_SOUNDS` turns them all off.
- **Cost:** the engine (21 nodes) spends ~0.04 ms of CPU for every 10 ms of sound, on the mixer's thread, without allocating memory.
```blueprint
Event Tick -> Set Float Parameter ( Target = EngineAudio, In Name = "RPM", In Float = CurrentRPM )
Event BeginPlay -> Set Float Parameter ( Target = RainAudio, In Name = "Intensity", In Float = 50 )
```
