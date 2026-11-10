id: render-styles
kind: howto
title: Estilo de render: estilizado, realista, fotorrealista, vídeo-realista | Render style: stylized, realistic, photorealistic, video-realistic
keys: ruido, noise, granulado, grain, grao, denoise, reduzir ruido, ghosting, contorno, outline, toon shading, faixas, bands, stop motion, animacao em dois, on twos, sombra colorida, cel shading, preset estilizado, cara de filmado, parecer filmado, camera real, cara de cinema, cara de video, visual realista, estilo de render, render style, estilizado, stylized, toon, cel, realista, fotorrealista, photoreal, video realista, video realistic, agx, aces, tonemapper, tone mapping, mapeamento de tom, camera fisica, halation, grao de filme, film grain, distorcao de lente, lens distortion, flashback, camera de seguranca, bodycam, set render style
--- pt
```diagram steps
Configurações do Projeto > Rendering > Render Style
Realista: o visual de sempre (ACES), o padrão
Fotorrealista: o tonemapper AgX (luz forte vai para o branco, sem estourar nas cores puras)
Vídeo-realista: AgX e a câmera de verdade (halation, grão, distorção, franjas, vinheta)
Estilizado: luz em faixas chapadas e cores mais fortes
```
O **estilo** diz **como o quadro fica**; a **escalabilidade** (Baixo a Épico) diz **quanto ele custa**. Os dois se combinam.
- **Onde:** Configurações do Projeto > Rendering > **Render Style**. O viewport do editor muda na hora. [Abrir as Configurações do Projeto](open:project)
- **Realista** é o visual que a engine sempre teve (ACES) e continua o padrão.
- **Fotorrealista** troca o mapeamento de tom pelo **AgX** (o do Blender): o céu e as luzes fortes vão para o branco como numa foto, em vez de saturar no amarelo ou no azul puros.
- **Vídeo-realista** é o AgX mais a **câmera física**: o halo vermelho do filme em volta das luzes fortes (halation), grão do sensor mais forte no escuro, a distorção de barril de uma lente real, franjas de cor nas bordas e vinheta. Os valores do Post Process Volume continuam valendo e só aumentam esses efeitos.
- **Estilizado** desenha a luz em faixas chapadas (mantém a cor) e deixa as cores mais fortes. Escolhido, aparece a seção **Estilizado** com tudo no seu controle: **Começar de um Preset** (Cel, Quadrinhos, Pintado, Stop-Motion, Toon), **Faixas** (2 = só luz e sombra), **Suavidade das Faixas** (0 cel duro, 1 pintado), **Tom das Sombras**, **Saturação**, **Contorno** (largura em px a 1440p, cor, sensibilidade pela profundidade) e **Taxa de Quadros da Animação** (12 = stop-motion "em dois"; o jogo continua no próprio FPS).
- **No jogo:** o nó **Set Render Style** troca o estilo em tempo de execução (um flashback estilizado, uma câmera de segurança vídeo-realista); **-1** volta ao do projeto. **Get Render Style** diz qual está em uso. Ao sair do Play o editor volta ao do projeto.
- **Custo:** o estilo só muda a composição final; o AgX e os efeitos de câmera custam menos de 0,05 ms a 1440p.
```blueprint
Event BeginPlay -> Set Render Style ( Style = 3 )
```
- **Ruído na imagem:** o Vídeo-realista põe **grão de filme** (muda a cada quadro, parece ruído). **Grão de Filme** (Configurações do Projeto > Rendering) regula: 0 deixa a imagem limpa. **Denoise** (Automático / Ligado / Desligado) filtra o ruído da luz por raio em qualquer estilo, só com o histórico do mesmo objeto, mesma direção e mesma profundidade (sem ghosting); precisa de ray tracing.
--- en
```diagram steps
Project Settings > Rendering > Render Style
Realistic: the look so far (ACES), the default
Photorealistic: the AgX tone mapper (strong light goes to white, not to pure colors)
Video-realistic: AgX and a real camera (halation, grain, distortion, fringes, vignette)
Stylized: light in flat bands and stronger colors
```
The **style** says **how the frame looks**; the **scalability** (Low to Epic) says **what it costs**. The two combine.
- **Where:** Project Settings > Rendering > **Render Style**. The editor's viewport changes at once. [Open the Project Settings](open:project)
- **Realistic** is the look the engine always had (ACES) and stays the default.
- **Photorealistic** swaps the tone mapping for **AgX** (Blender's): the sky and strong lights go to white like in a photo, instead of saturating into pure yellow or blue.
- **Video-realistic** is AgX plus the **physical camera**: film's red halo around strong lights (halation), sensor grain stronger in the dark, a real lens's barrel distortion, color fringes at the edges and vignette. The Post Process Volume's values still apply and only raise these effects.
- **Stylized** draws the light in flat bands (keeping its color) and makes colors stronger. Chosen, a **Stylized** section shows everything under your control: **Start From Preset** (Cel, Comic, Painted, Stop-Motion, Toon), **Bands** (2 = light and shadow only), **Band Softness** (0 hard cel, 1 painted), **Shadow Tint**, **Saturation**, **Outline** (width in px at 1440p, color, depth sensitivity) and **Animation Frame Rate** (12 = stop-motion "on twos"; the game keeps its own frame rate).
- **In the game:** the **Set Render Style** node changes the style while it runs (a stylized flashback, a video-realistic security camera); **-1** goes back to the project's. **Get Render Style** says which one is in use. Leaving Play brings the editor back to the project's.
- **Cost:** the style only changes the final composite; AgX and the camera effects cost under 0.05 ms at 1440p.
```blueprint
Event BeginPlay -> Set Render Style ( Style = 3 )
```
- **Noise in the picture:** Video-realistic adds **film grain** (it changes every frame, it reads as noise). **Film Grain** (Project Settings > Rendering) sets it: 0 gives a clean picture. **Denoise** (Automatic / On / Off) filters the traced light's noise in any style, keeping only the history of the same object, facing the same way, at the same depth (no ghosting); it needs ray tracing.
