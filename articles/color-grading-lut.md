id: color-grading-lut
kind: howto
title: LUT de correção de cor (Color Grading LUT) | Color Grading LUT
keys: lut, lut 3d, 3d lut, color grading lut, lut de cor, look, tabela de cor, color lookup table, .cube, arquivo cube, cube file, davinci resolve lut, photoshop lut, filtro de cor, color filter, grading de cinema, film look, aparencia de filme, color grading intensity
--- pt
```diagram steps
Faça o grading num programa (DaVinci Resolve, Photoshop, Premiere) e exporte um .cube
Coloque o arquivo dentro do Content do projeto (ex.: Content/LUTs/Filme.cube)
Post Process Volume > Color Grading LUT: escolha o arquivo (...) e ajuste a Intensity
```
Um **LUT 3D** guarda um visual inteiro de cor (o "look" de um filme, uma cena fria, um flashback sépia) e o aplica à imagem final, como o **Color Grading LUT** da Unreal.
- **Formatos aceitos:** **.cube** (DaVinci Resolve, Adobe, a maioria dos sites de LUT; tamanhos de 2 a 64) ou uma **faixa PNG** de N·N × N pixels, o formato da Unreal (256 × 16 para 16³).
- **Onde ele entra:** depois do tone mapping e dos outros ajustes do volume (balanço de branco, saturação, contraste), com as cores em sRGB, como nos programas de grading. A vinheta e o grão vêm depois.
- **Color Grading LUT Intensity** mistura o original com o LUT (0 a 1). Com vários volumes, vale o LUT do volume de maior prioridade em que a câmera está, multiplicado pelo peso dele.
- **Custo:** duas leituras de textura por pixel no composite. O arquivo é lido uma vez, quando muda.
--- en
```diagram steps
Grade the image in another program (DaVinci Resolve, Photoshop, Premiere) and export a .cube
Put the file inside the project's Content (e.g. Content/LUTs/Film.cube)
Post Process Volume > Color Grading LUT: pick the file (...) and set the Intensity
```
A **3D LUT** stores a whole color look (a film's look, a cold scene, a sepia flashback) and applies it to the final image, like Unreal's **Color Grading LUT**.
- **Accepted formats:** **.cube** (DaVinci Resolve, Adobe, most LUT sites; sizes 2 to 64) or a **PNG strip** of N·N × N pixels, Unreal's format (256 × 16 for 16³).
- **Where it applies:** after tone mapping and the volume's other adjustments (white balance, saturation, contrast), with the colors in sRGB, as in grading programs. The vignette and grain come after.
- **Color Grading LUT Intensity** blends the original with the LUT (0 to 1). With several volumes, the LUT of the highest priority volume the camera is in wins, multiplied by its weight.
- **Cost:** two texture reads per pixel in the composite. The file is read once, when it changes.
