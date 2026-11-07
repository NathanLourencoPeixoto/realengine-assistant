id: touch-controls
kind: recipe
title: Controles de toque: joystick virtual e botões | Touch controls: virtual joystick and buttons
keys: toque, touch, touch screen, tela de toque, joystick virtual, virtual joystick, analogico, thumbstick, botao de toque, touch button, area de olhar, look area, arrastar camera, drag camera, celular, mobile, android, multitouch, varios dedos, multiple fingers, WBP_TouchControls, controles mobile, mobile controls, hud mobile, vibrar, vibrate
--- pt
```diagram steps
Configurações do Projeto > Android > Controles de Toque (ligado) | O jogo cria Content/UI/WBP_TouchControls | Abra o WBP_TouchControls no Designer para mudar posições, tamanhos e cores | Paleta > Virtual Joystick / Touch Button / Touch Look Area para fazer o seu
```
## Os três widgets (Paleta do Widget Blueprint)
- **Virtual Joystick**: *Controla* **Move** (anda, como W/A/S/D) ou **Look** (gira a câmera). O pino segue o dedo dentro da base; zona morta pequena.
- **Touch Button**: a **Tecla** que ele segura enquanto é tocado (`Space`, `E`, `Shift`, `Escape`, `Left Mouse Button`...) e o **Rótulo** mostrado. Os eventos de tecla dos Blueprints e o Enhanced Input funcionam sem mudar nada. Tem os eventos *OnPressed* e *OnReleased* e vibra de leve no Android.
- **Touch Look Area**: invisível no jogo; arrastar dentro dela gira a câmera (*Graus por Pixel*).

Vários dedos ao mesmo tempo: cada dedo fica com o widget onde tocou até sair da tela. No PC o mouse faz papel de um dedo; teste no editor com a variável de ambiente `REALENGINE_TOUCH=1`.

O **WBP_TouchControls** pronto tem o joystick à esquerda, a área de olhar à direita, *Pular* (Espaço), *Usar* (E), *Correr* (Shift) e *Pausa* (Esc): as teclas que os Characters dos modelos já usam. Custo: 0,14 µs por quadro com 10 dedos.

```blueprint
Event BeginPlay -> Create Widget ( WBP_TouchControls ) -> Add to Viewport
```
Veja também [Exportar para Android](article:android-export) e [UI do jogo](article:game-ui).
--- en
```diagram steps
Project Settings > Android > Touch Controls (on) | The game makes Content/UI/WBP_TouchControls | Open WBP_TouchControls in the Designer to change positions, sizes and colors | Palette > Virtual Joystick / Touch Button / Touch Look Area to make your own
```
## The three widgets (the Widget Blueprint's Palette)
- **Virtual Joystick**: *Drives* **Move** (walks, like W/A/S/D) or **Look** (turns the camera). The knob follows the finger inside the base; a small dead zone.
- **Touch Button**: the **Key** it holds while touched (`Space`, `E`, `Shift`, `Escape`, `Left Mouse Button`...) and the **Label** shown. Blueprint key events and Enhanced Input work unchanged. It has *OnPressed* and *OnReleased* events and vibrates lightly on Android.
- **Touch Look Area**: invisible in the game; a drag inside it turns the camera (*Degrees per Pixel*).

Several fingers at once: each finger keeps the widget it landed on until it lifts. On the PC the mouse acts as one finger; test in the editor with the environment variable `REALENGINE_TOUCH=1`.

The ready **WBP_TouchControls** has the joystick on the left, the look area on the right, *Jump* (Space), *Use* (E), *Run* (Shift) and *Pause* (Esc): the keys the templates' Characters already use. Cost: 0.14 µs a frame with 10 fingers.

```blueprint
Event BeginPlay -> Create Widget ( WBP_TouchControls ) -> Add to Viewport
```
See also [Export to Android](article:android-export) and [Game UI](article:game-ui).
