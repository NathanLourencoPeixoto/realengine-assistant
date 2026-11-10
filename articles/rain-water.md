id: rain-water
kind: howto
title: Chuva, poças, córregos e oceano | Rain, puddles, streams and ocean
keys: escoamento, escorrer agua, runoff, agua escorrendo, molhar o plano, chuva, rain, chover, tempestade, storm, garoa, drizzle, molhado, wet, poca, puddle, poças, enchente, flood, alagado, rio, river, corrego, stream, escorrer, runoff, gotas, drops, respingo, splash, oceano, ocean, mar, sea, ondas, waves, espuma, foam, lago, lake, piscina, pool, agua, water, fft, barco flutuando, boat float, rastro, wake, neve, snow, nevar, nevasca, snowfall, flocos, flakes, inverno, winter, derreter, melt, cobertura de neve, snow cover, agua transparente, transparent water, raso, shallow, fundo do lago, lake bottom, espuma na margem, shore foam, praia, beach, refracao, refraction, causticas, caustics, luz no fundo da piscina, pool light lines, textura no fundo, pegadas, footprints, rastro na neve, snow trail, pisar na neve, chuva inclinada, vento, chuva com angulo, beiral, goteira, goteiras, drip, drips, borda molhada, quadrados molhados, wet edge
--- pt
```diagram steps
Adicionar Rápido > Chuva (o ator Rain) | Detalhes: Intensidade da Chuva, Molhado, Poças, Escoamento | Adicionar Rápido > Oceano (ou Water Body com Ocean ligado) | Play: barcos flutuam nas ondas, o que se mexe deixa rastro
```
## Chuva
Um ator **Rain** faz chover em volta da câmera:
- **Gotas** caindo com o vento e **respingos** onde batem; somem embaixo de telhados e árvores (a chuva "vê" a cena de cima por raios).
- As superfícies que a chuva alcança **molham** com o tempo (mais escuras e brilhantes) e **secam** quando ela para; embaixo de um telhado fica seco. Paredes ganham **água escorrendo**.
- A água **se acumula de verdade**: uma simulação de água rasa (tubos virtuais) faz a água correr morro abaixo, juntar em **poças** e, com chuva forte, virar **córregos** que quase viram rios. **Ganho de Água** acelera (1 = real); **Infiltração** e **Evaporação** tiram água; **Água Inicial** começa já alagado.
- Tudo é ajustável nos Detalhes; custa ~0,4 ms numa RTX 3060 em 1440p.

## Neve
Ligue **Snow** no mesmo ator Rain:
- **Flocos** caem devagar balançando no vento (**Tamanho do Floco**); a **Intensidade da Chuva** vira a força da nevasca.
- Uma **cobertura branca** junta no que fica virado para cima (chão, telhados, topo dos muros); embaixo de telhados fica sem neve. **Ângulo de Cobertura**: a inclinação máxima onde a neve fica. **Tempo de Cobertura**: quantos segundos de neve moderada até ficar todo branco.
- Quando para de nevar ela **derrete** (**Tempo de Derreter**; 0 = nunca) e a água escorre como a da chuva. **Cobertura Inicial**: um nível que já começa nevado.
- **Pegadas**: os Characters que andam na neve deixam pegadas, pé esquerdo e direito, com a borda de neve empurrada; a neve que continua caindo as cobre de novo. Sozinhas, sem configurar (uns 20 m em volta da câmera). ~0,03 ms.
- Por Blueprint: **Set Rain Intensity** liga e desliga a nevasca. ~0,3 ms.

## Oceano e lagos
- Um **Water Body** é desenhado como água (reflexo do céu, brilho do sol, cor funda, luz atravessando as cristas). Com **Ocean** ligado vira um **oceano sem fim**: ondas por FFT (o espectro do vento, JONSWAP), **espuma** onde quebram, **Agitação** e **Ondulação de Longe** ajustáveis. ~0,8 ms.
- **Barcos** flutuam nas ondas grandes; **veículos, personagens e corpos com física** fazem **anéis e rastros** na água (Interação).
- A chuva também faz anéis no oceano e nos lagos.
- **Água transparente** (Alto e Épico, com ray tracing): onde é raso o **fundo aparece** através da água, sumindo com a profundidade conforme a **Transparência** (o vermelho some primeiro: verde-azulado no raso, azul no fundo). **Espuma na Margem**: espuma branca nas praias e em volta de pedras e postes dentro da água. Cada lago tem a sua cor, transparência e espuma. O fundo aparece com a **textura** do material dele (e as linhas do M_Grid), e o sol forma **cáusticas**: a rede de linhas claras que as ondas desenham no fundo, nítidas no raso e espalhadas no fundo. ~0,35 ms a mais no Épico com água rasa na tela toda.
- **Chuva com vento:** a chuva cai inclinada pelo **vento** (Wind Speed e Direction do ator Rain) e o que ela alcança fica molhado: debaixo de um beiral do lado do vento molha, do outro lado fica seco. O lado de trás de uma parede fica seco.
- **Borda suave:** a passagem de molhado para seco é gradual (alguns centímetros, como os respingos fazem), sem quadrados nem faixa marcada.
- **Escoamento:** a água escorre pela superfície como a de verdade: desce as rampas e telhados até a borda (e cai) ou até um lugar plano, onde se espalha e junta nas partes mais baixas. Por onde ela passa fica molhado, mais quanto mais água passa, e continua molhado enquanto ainda escorre depois da chuva.
- **Goteiras:** bordas que juntam água (telhado, parapeito, galho) pingam gotas até o chão, e a água que escorre delas molha onde cai.

--- en
```diagram steps
Quick Add > Rain (the Rain actor) | Details: Rain Intensity, Wetness, Puddles, Flow | Quick Add > Ocean (or a Water Body with Ocean on) | Play: boats float on the waves, what moves leaves a wake
```
## Rain
A **Rain** actor makes it rain around the camera:
- **Drops** falling with the wind and **splashes** where they land; they stop under roofs and trees (the rain "sees" the scene from above with rays).
- The surfaces the rain reaches get **wet** over time (darker, glossier) and **dry** when it stops; under a roof it stays dry. Walls get **water running down**.
- The water **really gathers**: a shallow water simulation (virtual pipes) runs it downhill into **puddles** and, in heavy rain, **streams** that almost become rivers. **Water Gain** speeds it up (1 = real); **Infiltration** and **Evaporation** take water away; **Start Water** starts flooded.
- Everything is in the Details; it costs ~0.4 ms on an RTX 3060 at 1440p.

## Snow
Turn on **Snow** on the same Rain actor:
- **Flakes** fall slowly, fluttering in the wind (**Flake Size**); **Rain Intensity** becomes how hard it snows.
- A **white cover** gathers on what faces up (ground, roofs, wall tops); under roofs there is none. **Cover Angle**: the steepest surface the snow stays on. **Cover Time**: seconds of moderate snow until it is all white.
- When it stops it **melts** (**Melt Time**; 0 = never) and its water runs like the rain's. **Start Cover**: a level that starts snowed on.
- **Footprints**: Characters walking in the snow leave prints, left and right foot, with the rim of snow they push aside; the falling snow fills them back. On their own, nothing to set (about 20 m around the camera). ~0.03 ms.
- From a Blueprint: **Set Rain Intensity** starts and stops the snowfall. ~0.3 ms.

## Ocean and lakes
- A **Water Body** is drawn as water (the sky reflected, the sun's glints, the deep color, light through the crests). With **Ocean** on it becomes an **endless ocean**: FFT waves (the wind's spectrum, JONSWAP), **foam** where they break, adjustable **Choppiness** and **Swell**. ~0.8 ms.
- **Boats** float on the big waves; **vehicles, characters and physics bodies** make **rings and wakes** (Interaction).
- The rain makes rings on the ocean and the lakes too.
- **Transparent water** (High and Epic, with ray tracing): where it is shallow the **bottom shows** through the water, fading with the depth by its **Clarity** (red goes first: green-blue in the shallows, blue deeper). **Shore Foam**: white water on beaches and around rocks and posts standing in it. Each lake has its own color, clarity and foam. The bottom shows with its material's **texture** (and the M_Grid's lines), and the sun makes **caustics**: the net of bright lines the waves draw on the bottom, sharp in the shallows and spread out deeper. ~0.35 ms more on Epic with shallow water over the whole view.
- **Rain with wind:** the rain falls slanted by the **wind** (the Rain actor's Wind Speed and Direction) and what it reaches gets wet: under an eave on the windward side it wets, on the other side it stays dry. The back of a wall stays dry.
- **Soft edge:** wet turns to dry gradually (a few centimeters, as the splashes do), with no squares or hard stripe.
- **Runoff:** the water runs over the surface like real water: down ramps and roofs to the edge (and falls) or to a flat place, where it spreads and gathers in the low spots. Where it passes gets wet, more the more water passes, and stays wet while it still runs after the rain.
- **Drips:** edges that gather water (a roof, a ledge, a branch) drip drops down to the ground, and the water running off them wets where it lands.
