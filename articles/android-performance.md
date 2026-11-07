id: android-performance
kind: howto
title: Jogo liso no celular (Android) | A smooth game on phones (Android)
keys: android liso, celular travando, phone lag, mobile performance, desempenho celular, fps celular, resolucao dinamica, dynamic resolution, content scale, escala da tela, aquecendo, overheating, thermal, termica, bateria, battery, economia de bateria, battery saver, 30 fps, 60 fps, 120 fps, adpf, frame pacing, ritmo de quadros, qualidade mobile, mobile quality, segundo plano, background, minimizar, voltar ao jogo, memoria baixa, low memory
--- pt
```diagram steps
Configurações do Projeto > Android > Desempenho | Qualidade no Celular: Automática (ou Baixa, Média, Alta) | Taxa de Quadros Alvo: 30, 60, 90 ou 120 | Resolução Dinâmica ligada | Compilar > Empacotar para Android e jogar
```
## O que a engine faz sozinha no celular
- **Perfil do aparelho**: Baixa, Média ou Alta pela GPU (Adreno, Mali, Immortalis, Xclipse) e pela memória. Sem efeitos de raio, sombras e nuvens mais leves, neblina só na Alta.
- **Escala da tela** (como o `r.MobileContentScaleFactor` da Unreal): a janela é desenhada a 70, 80 ou 90% da tela e o sistema amplia sem custo. Toques e interface continuam no lugar certo.
- **Resolução dinâmica**: se o quadro passa do tempo, a resolução 3D desce em passos de 5% e volta a subir quando sobra folga. Fica estável, sem ficar subindo e descendo.
- **Ritmo de quadros**: a tela é avisada da taxa do jogo e cada quadro sai no tempo certo. Nenhum quadro é desenhado à toa (bateria e calor).
- **Calor**: a engine lê a folga térmica do Android. Antes de o celular reduzir o desempenho sozinho, ela baixa a resolução e, se esquentar mais, cai para metade da taxa.
- **Economia de bateria** ligada: 30 fps.
- **ADPF** (Android 13 ou mais novo): o sistema recebe o tempo de CPU de cada quadro e ajusta os clocks ao trabalho.
- **Segundo plano**: ao sair do jogo o áudio é solto e nada é desenhado. Ao voltar, a tela é refeita e o jogo continua de onde estava.
- **Memória**: as texturas têm um orçamento pela qualidade e cedem um quarto quando o Android avisa que a memória está acabando.

## Medir
No logcat (`adb logcat -s RealEngine`), a cada 5 s: fps, CPU, GPU, resolução e temperatura. Para testar no aparelho:
- `adb shell setprop debug.realengine.tier 1` força a qualidade Baixa (2 Média, 3 Alta);
- `adb shell setprop debug.realengine.fps 30` muda a taxa de quadros;
- `adb shell setprop debug.realengine.mobile 0` desliga o perfil (para comparar).

No PC, o mesmo perfil roda com `REALENGINE_MOBILE=1`. Veja também [Exportar para Android](article:android-export).
--- en
```diagram steps
Project Settings > Android > Performance | Mobile Quality: Automatic (or Low, Medium, High) | Target Frame Rate: 30, 60, 90 or 120 | Dynamic Resolution on | Build > Package for Android and play
```
## What the engine does by itself on a phone
- **Device profile**: Low, Medium or High by the GPU (Adreno, Mali, Immortalis, Xclipse) and the memory. No traced effects, lighter shadows and clouds, fog only on High.
- **Screen scale** (like Unreal's `r.MobileContentScaleFactor`): the window is drawn at 70, 80 or 90% of the screen and the system upscales it for free. Touches and the UI stay in the right place.
- **Dynamic resolution**: when a frame runs late, the 3D resolution drops in 5% steps and climbs back when there is room. It settles instead of bouncing up and down.
- **Frame pacing**: the display is told the game's rate and each frame goes out on time. No frame is drawn for nothing (battery and heat).
- **Heat**: the engine reads Android's thermal headroom. Before the phone throttles on its own, it lowers the resolution, and if it gets hotter it drops to half the rate.
- **Battery saver** on: 30 fps.
- **ADPF** (Android 13 or newer): the system gets each frame's CPU time and matches the clocks to the work.
- **Background**: leaving the game lets the audio device go and draws nothing. Coming back rebuilds the screen and the game carries on where it was.
- **Memory**: textures get a budget by quality and give back a quarter when Android warns that memory is running out.

## Measure
In logcat (`adb logcat -s RealEngine`), every 5 s: fps, CPU, GPU, resolution and temperature. To test on a device:
- `adb shell setprop debug.realengine.tier 1` forces Low quality (2 Medium, 3 High);
- `adb shell setprop debug.realengine.fps 30` changes the frame rate;
- `adb shell setprop debug.realengine.mobile 0` turns the profile off (to compare).

On the PC, the same profile runs with `REALENGINE_MOBILE=1`. See also [Export to Android](article:android-export).
