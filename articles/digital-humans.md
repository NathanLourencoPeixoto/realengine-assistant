id: digital-humans
kind: concept
title: Pele e olhos realistas (humanos digitais) | Realistic skin and eyes (digital humans)
keys: olho, olhos, eye, eyes, iris, íris, cornea, córnea, pupila, pupil, esclera, sclera, olho de vidro, Shading Model, modelo de sombreamento, Eye shading model, M_Eye, SM_Eye, pele, skin, subsurface, subsuperficie, sss, subsurface scattering, espalhamento, burley, subsurface profile, perfil de subsuperficie, humano digital, digital human, metahuman, rosto, face, orelha contra a luz, ear backlit, ear glow, ear glows red, light behind the ear, backlight, backlit skin, contraluz, luz por tras da orelha, orelha vermelha, red glow, transmissao, transmission, dedo vermelho contra a luz, pele de cera, waxy skin, pele de plastico, plastic skin, Subsurface Weight, Subsurface Radius, Subsurface Scale, M_HumanSkin, REALENGINE_NO_SSS
--- pt
```diagram steps
O material tem Subsurface Weight e Subsurface Scale acima de 0
Pixels pares: só a luz difusa; ímpares: o brilho (xadrez)
Uma passada espalha a luz difusa pelo perfil de Burley de cada cor
A luz atrás de uma parte fina (orelha, dedo) atravessa
```
A luz entra na pele, espalha por dentro e sai um pouco ao lado: é o que tira o aspecto de plástico de um rosto. A engine faz isso **em tela**, como o Subsurface Profile da Unreal.
- **Como usar:** no nó **Principled BSDF** do material, ponha **Subsurface Weight** em 1, **Subsurface Radius** com a cor que espalha mais (pele: 1, 0.2, 0.1, o vermelho vai mais longe) e **Subsurface Scale** em metros (pele: 0.01 a 0.015). O exemplo pronto é `Examples/M_HumanSkin`. O padrão do Blender (0.05) deixa a pele parecendo cera.
- **Transmissão:** com uma luz atrás, uma orelha, um dedo ou a asa do nariz ficam vermelhos (um raio mede a espessura). Precisa de ray tracing (Médio para cima).
- **Custo** (RTX 3060, Épico, a cena `skin`): a passada 0,13 ms; só existe quando um material com subsuperfície aparece. As amostras sobem com o preset (Baixo 6, Médio 8, Alto 12, Épico 16).
- **Onde não liga:** com MSAA (o preset Cinemático) e com Variable Rate Shading a pele volta ao modelo antigo (a luz contorna o terminador).
- Para comparar sem: `REALENGINE_NO_SSS=1`; para ver o xadrez cru: `REALENGINE_SSS_RAW=1`.

**Olhos:** no editor do material, **Shading Model = Eye** (como na Unreal).
- A **córnea** vira uma camada transparente e molhada sobre o olho todo (o reflexo nítido do céu e das luzes).
- A **íris** fica embaixo dela e é vista **refratada**: muda de lugar quando a câmera gira, como num olho de verdade.
- A íris é iluminada como um **prato raso**: a luz que entra por um lado se junta no lado oposto (a cáustica).
- **Malha:** a íris no centro do UV (0,5, 0,5), com **Iris Radius** o raio em UV e **Iris Depth** a altura da córnea em cm. O olho olha para a frente do ator (+X).
- **Prontos:** a malha `Examples/SM_Eye` e o material `Examples/M_Eye`; a cena de teste `eyes` mostra os dois numa cabeça.
- **Pálpebras:** a sombra delas vem das sombras normais (por raio).
--- en
```diagram steps
The material has Subsurface Weight and Subsurface Scale above 0
Even pixels: only the diffuse light; odd ones: the shine (a checkerboard)
One pass spreads the diffuse light by each color's Burley profile
Light behind a thin part (an ear, a finger) comes through
```
Light enters the skin, scatters inside and leaves a little to the side: that is what takes the plastic look off a face. The engine does it **in screen space**, like Unreal's Subsurface Profile.
- **How to use:** on the material's **Principled BSDF** node, set **Subsurface Weight** to 1, **Subsurface Radius** to the color that scatters farther (skin: 1, 0.2, 0.1, red goes farthest) and **Subsurface Scale** in meters (skin: 0.01 to 0.015). The ready example is `Examples/M_HumanSkin`. Blender's default (0.05) makes skin look like wax.
- **Transmission:** with a light behind, an ear, a finger or a nostril's wing turn red (a ray measures the thickness). Needs ray tracing (Medium and up).
- **Cost** (RTX 3060, Epic, the `skin` scene): the pass 0.13 ms; it only exists when a subsurface material shows up. The samples grow with the preset (Low 6, Medium 8, High 12, Epic 16).
- **Where it's off:** with MSAA (the Cinematic preset) and with Variable Rate Shading the skin goes back to the old model (light wrapping past the terminator).
- To compare without it: `REALENGINE_NO_SSS=1`; to see the raw checkerboard: `REALENGINE_SSS_RAW=1`.

**Eyes:** in the material editor, **Shading Model = Eye** (as in Unreal).
- The **cornea** becomes a clear, wet layer over the whole eye (the sharp reflection of the sky and the lights).
- The **iris** lies under it and is seen **refracted**: it shifts as the camera turns, as a real eye's does.
- The iris is lit like a **shallow dish**: light coming in from one side pools on the far side (the caustic).
- **Mesh:** the iris at the UV's center (0.5, 0.5), **Iris Radius** its radius in UV and **Iris Depth** the cornea's height in cm. The eye looks along its actor's forward (+X).
- **Ready to use:** the mesh `Examples/SM_Eye` and the material `Examples/M_Eye`; the `eyes` test scene shows both on a head.
- **Eyelids:** their shadow comes from the normal (ray traced) shadows.
