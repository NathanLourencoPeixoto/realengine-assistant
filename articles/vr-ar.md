id: vr-ar
kind: howto
title: VR e AR: headset, controles e luz que combina com a câmera | VR and AR: headset, controllers and light matching the camera
keys: vr, realidade virtual, virtual reality, ar, realidade aumentada, augmented reality, headset, oculus, quest, meta, steamvr, openxr, controle de vr, motion controller, hmd, oculos, giroscopio, gyroscope, light estimation, estimar luz, color matching, balanco de branco, white balance, haptico, haptic, vibrar controle, arcore, rastreamento, tracking, 6dof, planos, planes, chao real, real floor, shadow catcher, oclusao, occlusion, profundidade, depth, depth api, objeto real na frente, esconder atras do sofa, sombra no chao real, camera do celular, phone camera, ar line trace, tocar na tela para colocar, tap to place, event touch, toque na tela, touch screen, get mouse position, template de ar, ar template
--- pt
```diagram steps
Empacote o jogo | Conecte o headset (Quest Link, SteamVR...) | Jogo.exe --vr (sem headset: --vr-sim mostra os dois olhos) | Blueprint: Get HMD Pose, Get Motion Controller Pose/Input, Play Haptic Effect
```
## VR
- A engine fala **OpenXR** direto com o runtime instalado (Meta, SteamVR, WMR): não precisa de SDK.
- Cada olho é renderizado com o motor inteiro, com **MSAA 4×** (o que tem histórico de tela fica desligado no VR para não misturar os olhos). Meta: **acima de 100 fps**: diminua a escalabilidade se a cena for pesada.
- Controles: **Get Motion Controller Pose** (lugar e direção), **Get Motion Controller Input** (gatilho, grip, analógico, botões), **Play Haptic Effect** (vibração), **Get HMD Pose**, **Is VR Active**.
```blueprint
Event Tick -> Get Motion Controller Input ( 1 ) -> Branch ( Trigger > 0.5 ) -> Play Haptic Effect ( 1, 0.6, 0.1 )
```
## AR
- **Luz e cor iguais às da câmera**: a engine mede a exposição, o balanço de branco (temperatura de cor), a luz principal (de onde vem e quão forte) e a luz ambiente da imagem, e aplica no sol, no céu e na exposição; os objetos virtuais ficam com a luz real.
- No celular, o **giroscópio** gira a câmera (`--ar`). No PC dá para testar com uma foto: `Jogo.exe --ar-image foto.png`.

## AR com ARCore (Android)
```diagram steps
Project Settings > Android > Realidade Aumentada (ARCore) | Compilar > Empacotar para Android | No celular: permitir a câmera, mover devagar sobre uma superfície | O jogo aparece no mundo real: rastreado, sobre o chão de verdade, com a sombra nele
```
- O celular é **rastreado em 6 graus de liberdade**: a câmera do jogo é a do celular, andando pelo quarto.
- A **imagem da câmera** fica atrás do nível; os objetos virtuais ficam na frente com a luz do lugar (direção, cor e intensidade estimadas pela ARCore).
- Os **planos** que a ARCore acha (chão, mesas, paredes) viram atores **AR Plane** que bloqueiam: os personagens andam no chão de verdade. O chão real **recebe as sombras** dos objetos virtuais (e o escurecido de contato embaixo deles).
- **Oclusão**: uma coisa real mais perto que uma virtual a esconde (o sofá na frente do cachorro virtual), pela profundidade da ARCore nos celulares que a têm. Project Settings > Android > **Oclusão pelos Objetos Reais** (ligada por padrão). No PC, `REALENGINE_AR_SIM_FLOOR=60` sobe o chão simulado 60 cm: a base dos objetos some atrás dele.
- Para começar pronto: **Novo Projeto > Realidade Aumentada** (a `BP_ARPlacer` põe uma caixa onde você toca no chão real; o AR já vem ligado).
- O toque: **Event Touch** (Pressed / Released, Location em pixels, Finger Index; no PC o botão esquerdo do mouse é um dedo) e **Get Mouse Position**. Os dedos que um widget de toque pegou (joystick, botão) não disparam o evento.
- Nós: **Is AR Tracking**, **AR Line Trace** (um ponto da tela no mundo real: colocar algo onde o jogador toca) e **Get AR Plane Count**.
- O AR é **opcional**: celulares sem o Google Play Services para AR rodam o jogo normalmente. No PC: `Jogo.exe --ar-image foto.png --ar-sim` simula (a foto atrás, um chão na origem).
```blueprint
Event Touch (Pressed) -> Break Vector ( Location ) -> AR Line Trace ( X, Y ) -> Branch ( Hit ) -> Spawn Actor from Class ( BP_Cadeira, Location )
```
--- en
```diagram steps
Package the game | Connect the headset (Quest Link, SteamVR...) | Game.exe --vr (no headset: --vr-sim shows both eyes) | Blueprint: Get HMD Pose, Get Motion Controller Pose/Input, Play Haptic Effect
```
## VR
- The engine talks **OpenXR** directly to the installed runtime (Meta, SteamVR, WMR): no SDK needed.
- Each eye is rendered by the whole engine with **MSAA 4x** (what keeps a screen history is off in VR so the eyes don't mix). Target: **above 100 fps**: lower the scalability if the scene is heavy.
- Controllers: **Get Motion Controller Pose** (place and direction), **Get Motion Controller Input** (trigger, grip, thumbstick, buttons), **Play Haptic Effect** (vibration), **Get HMD Pose**, **Is VR Active**.
```blueprint
Event Tick -> Get Motion Controller Input ( 1 ) -> Branch ( Trigger > 0.5 ) -> Play Haptic Effect ( 1, 0.6, 0.1 )
```
## AR
- **Light and color like the camera's**: the engine measures the picture's exposure, white balance (color temperature), main light (where from and how strong) and ambient light, and applies them to the sun, the sky and the exposure; virtual objects get the real light.
- On a phone the **gyroscope** turns the camera (`--ar`). On a PC test it with a photo: `Game.exe --ar-image photo.png`.

## AR with ARCore (Android)
```diagram steps
Project Settings > Android > Augmented Reality (ARCore) | Build > Package for Android | On the phone: allow the camera, move slowly over a surface | The game stands in the real world: tracked, on the real floor, casting its shadow on it
```
- The phone is **tracked with 6 degrees of freedom**: the game's camera is the phone's, walking around the room.
- The **camera's picture** is behind the level; the virtual things stand in front of it with the place's light (direction, color and strength estimated by ARCore).
- The **planes** ARCore finds (floors, tables, walls) become blocking **AR Plane** actors: the Characters walk on the real floor. The real floor **receives the shadows** of the virtual things (and the contact darkening under them).
- **Occlusion**: a real thing nearer than a virtual one hides it (the sofa in front of the virtual dog), from ARCore's depth on the phones that have it. Project Settings > Android > **Occlusion by Real Objects** (on by default). On a PC, `REALENGINE_AR_SIM_FLOOR=60` raises the simulated floor 60 cm: the things' bases hide behind it.
- Ready to start: **New Project > Augmented Reality** (`BP_ARPlacer` places a box where you touch the real floor; AR already on).
- The touch: **Event Touch** (Pressed / Released, Location in pixels, Finger Index; on a PC the left mouse button is a finger) and **Get Mouse Position**. The fingers a touch widget took (joystick, button) don't fire it.
- Nodes: **Is AR Tracking**, **AR Line Trace** (a point of the screen onto the real world: place something where the player taps) and **Get AR Plane Count**.
- AR is **optional**: phones without Google Play Services for AR run the game as usual. On a PC: `Game.exe --ar-image photo.png --ar-sim` simulates it (the photo behind, a floor at the origin).
```blueprint
Event Touch (Pressed) -> Break Vector ( Location ) -> AR Line Trace ( X, Y ) -> Branch ( Hit ) -> Spawn Actor from Class ( BP_Chair, Location )
```
