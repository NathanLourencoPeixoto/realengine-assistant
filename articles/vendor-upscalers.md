id: vendor-upscalers
kind: concept
title: DLSS, FSR e XeSS no lugar do TSR | DLSS, FSR and XeSS in TSR's place
keys: dlss, nvidia dlss, ligar o dlss, ativar dlss, usar dlss, turn on dlss, enable dlss, fsr, amd fsr, fidelityfx, xess, intel xess, upscaler, escolher upscaler, choose upscaler, rtx, transformer, dlaa, native aa, nvngx_dlss.dll, amd_fidelityfx_vk.dll, libxess.dll, em cinza, greyed, nao aparece, upscaler indisponivel, unavailable upscaler, custo do upscaler, upscaler cost
--- pt
```diagram bars ms
TSR: 0.44
AMD FSR 3.1: 1.6
NVIDIA DLSS (preset K): 2.2
Intel XeSS (DP4a): 2.6
```
Além do **TSR** da engine, o upscale pode ser feito pelo **NVIDIA DLSS**, pelo **AMD FSR 3.1** ou pelo **Intel XeSS**. Eles recebem a mesma imagem (a cena na resolução menor, a profundidade e o movimento de cada pixel) e entregam a imagem na resolução da tela. O gráfico mostra o custo de cada um numa RTX 3060, de 1294×798 para 2156×1330.
- **Onde escolher**: Configurações do Projeto > Rendering > **Upscaler**. O **Modo de Upscaling** (Qualidade, Equilibrado, Desempenho...) e a **Resolução Dinâmica** valem para todos. [Abrir as Configurações do Projeto](open:project)
- **Em cinza, com o motivo?** O DLSS precisa de uma placa NVIDIA RTX. O FSR e o XeSS rodam em qualquer placa com Vulkan 1.3. Os três precisam da DLL do fabricante ao lado do executável: `nvngx_dlss.dll`, `amd_fidelityfx_vk.dll` ou `libxess.dll`.
- **Qual usar**: o TSR é o mais barato e o mais estável parado. O DLSS reconstrói melhor os detalhes finos em resoluções baixas: no modo Desempenho (50%) ele fica mais nítido que o TSR em Qualidade (67%) e ainda roda mais rápido na cena pesada (82 contra 69 fps). O FSR é o mais leve dos três. O XeSS fica mais leve nas placas Intel Arc.
- Se um deles falhar na sua placa, o TSR assume sozinho e o Registro de Saída diz por quê.
- **Empacotar Jogo** leva junto a DLL do upscaler escolhido e a licença dela. O jogador sem a placa certa usa o TSR.
- Para comparar: `--upscaler tsr|fsr|dlss|xess` na linha de comando. [Linha de comando](article:command-line)
- O custo aparece em Reconstrução, no orçamento do quadro do Debug Viewer (F10). [Abrir](open:debug)
- Veja também [TSR: resolução menor, imagem nítida](article:tsr-upscaling).
--- en
```diagram bars ms
TSR: 0.44
AMD FSR 3.1: 1.6
NVIDIA DLSS (preset K): 2.2
Intel XeSS (DP4a): 2.6
```
Besides the engine's **TSR**, the upscale can be done by **NVIDIA DLSS**, **AMD FSR 3.1** or **Intel XeSS**. They take the same picture (the scene at the lower resolution, the depth and each pixel's motion) and give back the image at the screen's resolution. The chart shows each one's cost on an RTX 3060, from 1294×798 to 2156×1330.
- **Where to choose**: Project Settings > Rendering > **Upscaler**. The **Upscaling Mode** (Quality, Balanced, Performance...) and **Dynamic Resolution** apply to all of them. [Open the Project Settings](open:project)
- **Greyed, with a reason?** DLSS needs an NVIDIA RTX card. FSR and XeSS run on any card with Vulkan 1.3. All three need the vendor's DLL beside the executable: `nvngx_dlss.dll`, `amd_fidelityfx_vk.dll` or `libxess.dll`.
- **Which one**: TSR is the cheapest and the steadiest at rest. DLSS rebuilds fine detail best at low resolutions: in Performance mode (50%) it is sharper than TSR in Quality (67%) and still faster in the heavy scene (82 against 69 fps). FSR is the lightest of the three. XeSS is lighter on Intel Arc cards.
- If one fails on your card, TSR takes over by itself and the Output Log says why.
- **Package Game** takes the chosen upscaler's DLL and its license along. A player without the right card gets TSR.
- To compare: `--upscaler tsr|fsr|dlss|xess` on the command line. [Command line](article:command-line)
- The cost shows under Reconstruction, in the Debug Viewer's frame budget (F10). [Open](open:debug)
- See also [TSR: a lower resolution, a sharp image](article:tsr-upscaling).
