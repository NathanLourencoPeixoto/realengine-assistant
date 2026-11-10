id: cine-camera
kind: howto
title: Câmera de cinema: lente, ISO, obturador e bokeh | Cine camera: lens, ISO, shutter and bokeh
keys: cine camera, camera de cinema, camera fisica, physical camera, iso, obturador, shutter speed, velocidade do obturador, abertura, aperture, f-stop, distancia focal, focal length, lente, lens, sensor, filmback, super 35, full frame, bokeh, laminas do diafragma, diaphragm blades, exposicao manual, manual exposure, sunny 16, profundidade de campo fisica, physical depth of field, 180 graus, 180 degree shutter
--- pt
```diagram steps
Selecione o Camera Actor (ou o componente Camera do personagem)
Details > Camera: ligue Physical Lens, Manual Exposure e/ou Motion Blur from Shutter
Escolha os presets (Filmback, Lens, Exposure) ou digite os valores
```
A câmera vira uma **câmera de cinema**, como o Cine Camera Actor da Unreal, enquanto é a vista do jogador (Play ou jogo):
- **Physical Lens:** a **distância focal** e a **largura do sensor** dão o campo de visão (50 mm num Super 35: 28°). **Abertura** e **Focus Distance** dão a profundidade de campo física, com o círculo de confusão f²/(N·(S − f)) no sensor, em pixels. **Diaphragm Blades** de 5 a 9 deixam o bokeh poligonal, como numa lente real; 0 deixa redondo.
- **Manual Exposure:** a exposição sai de **ISO**, **Shutter Speed** e abertura: EV100 = log2(N²/t) − log2(ISO/100). O "Sunny 16" (ISO 100, f/16, 1/125) dá 14,97, a luz do sol. A Exposure Compensation dos volumes continua somando, como na Unreal.
- **Motion Blur from Shutter:** o borrão de movimento sai do tempo do obturador (1/48 a 24 fps é o obturador de 180° do cinema).
- **Presets:** Filmback (Full Frame, Super 35, APS-C, Micro 4/3, Super 16, IMAX), Lens (12 a 200 mm) e Exposure (Sunny 16, Nublado, Interno, Rua à noite, Cinema 180°).
--- en
```diagram steps
Select the Camera Actor (or the character's Camera component)
Details > Camera: turn on Physical Lens, Manual Exposure and/or Motion Blur from Shutter
Pick the presets (Filmback, Lens, Exposure) or type the values
```
The camera becomes a **cinema camera**, like Unreal's Cine Camera Actor, while it is the player's view (Play or the game):
- **Physical Lens:** the **focal length** and the **sensor width** give the field of view (50 mm on Super 35: 28°). **Aperture** and **Focus Distance** give a physical depth of field, with the circle of confusion f²/(N·(S − f)) on the sensor, in pixels. **Diaphragm Blades** from 5 to 9 make the bokeh a polygon, as with a real lens; 0 keeps it round.
- **Manual Exposure:** the exposure comes from **ISO**, **Shutter Speed** and aperture: EV100 = log2(N²/t) − log2(ISO/100). "Sunny 16" (ISO 100, f/16, 1/125) gives 14.97, sunlight. The volumes' Exposure Compensation still adds on top, as in Unreal.
- **Motion Blur from Shutter:** the motion blur comes from the shutter time (1/48 at 24 fps is cinema's 180° shutter).
- **Presets:** Filmback (Full Frame, Super 35, APS-C, Micro 4/3, Super 16, IMAX), Lens (12 to 200 mm) and Exposure (Sunny 16, Overcast, Indoor, Night Street, Cinema 180°).
