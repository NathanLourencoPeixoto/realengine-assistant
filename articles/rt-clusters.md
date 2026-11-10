id: rt-clusters
kind: concept
title: Ray tracing por clusters (Mega Geometry) | Cluster ray tracing (Mega Geometry)
keys: mega geometry, rtx mega geometry, clusters, cluster acceleration structure, clas, blas, tlas, memoria do ray tracing, ray tracing memory, memoria de rt, vram do ray tracing, estrutura de aceleracao, acceleration structure, malha pesada ray tracing, heavy mesh ray tracing, nanite ray tracing, REALENGINE_NO_CLAS, VK_NV_cluster_acceleration_structure
--- pt
```diagram steps
Cada malha estática cortada em clusters de 64 a 128 triângulos
Cada cluster vira uma CLAS comprimida pelo driver
Uma BLAS por malha aponta para os clusters dela
O raio acha o triângulo pelo índice de geometria (igual ao clássico)
```
Nas placas **NVIDIA RTX** com o driver novo, as estruturas de ray tracing das malhas estáticas são feitas de **clusters** (a técnica que a NVIDIA chama de RTX Mega Geometry e que o DXR padronizou em 2026). É automático: não há nada para ligar.
- **Menos memória de vídeo:** a cena `heavy` (2,1 milhões de triângulos) foi de 143 MB para 59 MB de BLAS (−59%); a casa −69%; a RPG −43%.
- **Mesma velocidade ou melhor:** os clusters saem do construtor espacial do meshoptimizer (pensado para ray tracing); a RPG ficou ~7% mais rápida, a heavy igual. A imagem é a mesma.
- **Em outras placas** (AMD, Intel, Android) ou com `REALENGINE_NO_CLAS=1` ficam as BLAS clássicas, sem diferença na imagem.
- O que se deforma (tecido, personagens, multidões) continua com as BLAS dinâmicas de sempre.
- **Ainda não:** o raio usa o LOD 0 de cada malha (o raster usa o corte de LOD); BLAS por instância com o mesmo corte e a TLAS particionada vêm depois.
--- en
```diagram steps
Each static mesh cut into clusters of 64 to 128 triangles
Each cluster becomes a CLAS compressed by the driver
One BLAS per mesh points at its clusters
The ray finds the triangle by the geometry index (same as classic)
```
On **NVIDIA RTX** cards with a recent driver, the static meshes' ray tracing structures are made of **clusters** (what NVIDIA calls RTX Mega Geometry, standardized by DXR in 2026). It's automatic: nothing to turn on.
- **Less video memory:** the `heavy` scene (2.1 million triangles) went from 143 MB to 59 MB of BLAS (−59%); the house −69%; the RPG −43%.
- **Same speed or better:** the clusters come from meshoptimizer's spatial builder (made for ray tracing); the RPG got ~7% faster, heavy the same. The image is identical.
- **On other cards** (AMD, Intel, Android) or with `REALENGINE_NO_CLAS=1` the classic BLAS stay, with no difference in the image.
- What deforms (cloth, characters, crowds) keeps the usual dynamic BLAS.
- **Not yet:** the ray sees each mesh's LOD 0 (the raster uses the LOD cut); per-instance BLAS with the same cut and the partitioned TLAS come later.
