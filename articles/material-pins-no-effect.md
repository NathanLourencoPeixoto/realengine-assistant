id: material-pins-no-effect
kind: concept
title: Verniz, vidro, subsuperfície e os pinos "ainda sem efeito" | Coat, glass, subsurface and the "no effect yet" inputs
keys: veludo, velvet, sheen, iridescencia, iridescence, bolha de sabao, soap bubble, pelicula fina, thin film, sem efeito, ainda sem efeito, pino cinza, entrada cinza, verniz, clearcoat, coat, transmissao, transmission, vidro, subsurface, subsuperficie, pele, anisotropico, anisotropic, metal escovado, brushed metal, sheen, aveludado, specular tint, thin film, ior, glossy, no effect yet, greyed input, pintura de carro, car paint, masked transmissao, cabelo transmissao, alpha e transmissao, hair transmission
--- pt
```diagram steps
Principled BSDF: os pinos com valor (sem ligação)
O material assa cor, normal, rugosidade e metálico por texel
Coat, Anisotropic, Subsurface, Specular, IOR e Transmission viram constantes do material
O shader soma o verniz, estica o brilho, deixa a luz atravessar a pele, vira vidro
```
O **Principled BSDF** tem todos os pinos do Blender. Por texel (podem receber texturas e nós): **Base Color, Metallic, Roughness, Alpha, Normal, Emission Color e Emission Strength**.
- **Como valor do material** (um número ou cor no pino, sem ligação):
  - **Coat** (Weight, Roughness, IOR, Tint): uma camada de verniz por cima, com brilho próprio na normal da superfície (o normal map fica por baixo). Pintura de carro, madeira envernizada.
  - **Anisotropic** e **Anisotropic Rotation**: o brilho esticado ao longo do UV, como metal escovado.
  - **Subsurface** (Weight, Radius, Scale): a luz passa do terminador mais nos canais de raio maior (pele: o vermelho), sem a sombra dura.
  - **IOR**, **Specular IOR Level** e **Specular Tint**: o reflexo dos não metais (água 1,33, vidro 1,5, diamante 2,4).
  - **Transmission Weight**: o material passa a ser desenhado como translúcido (vidro), deixando passar essa parte da luz.
  - **Sheen** (Weight, Roughness, Tint): o brilho claro na borda de tecidos como veludo e de superfícies empoeiradas.
  - **Thin Film** (Thickness em nm, IOR): as cores de bolha de sabão, óleo na água, lente com tratamento.
- **Ligou um nó ou textura** num desses pinos? Por enquanto só o valor conta: o pino fica **em cinza** e o nó ganha o **"!" laranja**.
- **Ainda sem efeito**: Diffuse Roughness, Coat Normal e os pinos de Subsurface IOR/Anisotropy. O valor fica salvo para quando existirem.
- Um glTF com verniz, transmissão ou sheen avisa no Registro de Saída ao importar.
- No **Glossy BSDF** valem Color, Roughness e Normal. [Vidro e translúcidos](article:glass-translucent)
- **Masked, Two Sided e Translucent:** os lóbulos extras (IOR, subsuperfície, especular, anisotropia, coat) funcionam em materiais **Opaque**, **Masked** e **Two Sided** (cabelo, folhas, cartões com coat ou brilho anisotrópico). Só no **Translucent** os pinos ficam cinza. Num **Masked** a **Transmissão** não vira vidro: o recorte pelo Alpha vale. Voltar a Transmissão para 0 devolve o material ao normal na hora.

--- en
```diagram steps
Principled BSDF: the inputs with a value (no link)
The material bakes color, normal, roughness and metallic per texel
Coat, Anisotropic, Subsurface, Specular, IOR and Transmission become the material's constants
The shader adds the coat, stretches the highlight, lets light through skin, turns it into glass
```
The **Principled BSDF** has all of Blender's inputs. Per texel (they take textures and nodes): **Base Color, Metallic, Roughness, Alpha, Normal, Emission Color and Emission Strength**.
- **As the material's value** (a number or color in the input, no link):
  - **Coat** (Weight, Roughness, IOR, Tint): a varnish layer on top, with its own highlight on the surface's normal (the normal map stays under it). Car paint, varnished wood.
  - **Anisotropic** and **Anisotropic Rotation**: the highlight stretched along the UV, like brushed metal.
  - **Subsurface** (Weight, Radius, Scale): light passes the terminator, farther in the channels with a bigger radius (skin: red), without the hard shadow edge.
  - **IOR**, **Specular IOR Level** and **Specular Tint**: the reflection of non-metals (water 1.33, glass 1.5, diamond 2.4).
  - **Transmission Weight**: the material is drawn as translucent (glass), letting that share of the light through.
  - **Sheen** (Weight, Roughness, Tint): the light rim on the edge of fabrics like velvet and of dusty surfaces.
  - **Thin Film** (Thickness in nm, IOR): the colors of a soap bubble, oil on water, a coated lens.
- **Linked a node or texture** into one of those? For now only the value counts: the input shows **greyed** and the node gets the **orange "!"**.
- **No effect yet**: Diffuse Roughness, Coat Normal and the Subsurface IOR/Anisotropy inputs. The value is saved for when they exist.
- A glTF with clearcoat, transmission or sheen says so in the Output Log when imported.
- In the **Glossy BSDF**, Color, Roughness and Normal count. [Glass and translucency](article:glass-translucent)
- **Masked, Two Sided and Translucent:** the extra lobes (IOR, subsurface, specular, anisotropy, coat) work on **Opaque**, **Masked** and **Two Sided** materials (hair, leaves, cards with a coat or an anisotropic sheen). Only on **Translucent** are their pins grey. On a **Masked** one **Transmission** doesn't make it glass: the cut by the Alpha wins. Setting Transmission back to 0 brings the material back at once.
