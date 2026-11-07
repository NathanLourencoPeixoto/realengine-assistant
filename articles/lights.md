id: lights
kind: howto
title: Luzes e Build Lighting | Lights and Build Lighting
keys: luz, iluminacao, lampada, sol, sombra, build lighting, assar luz, bake, lux, point light, spot light, directional, sky light
--- pt
```diagram compare
 | Parece | Bom para
Directional | o sol | dia, exterior
Point | uma lâmpada | luminárias, tochas
Spot | uma lanterna | holofotes, faróis
Rect | uma janela, um painel | interiores
Sky | o céu inteiro | o ambiente
```
## Adicionar uma luz
- **Ator > Adicionar** tem Directional (o sol), Point, Spot, Rect e Sky Light. [Adicionar uma Point Light](add:Point Light) [Mostrar onde](show:Actor>Add)
- A intensidade usa unidades físicas (lux, candela); o painel Details mostra cada campo.

## Luz assada (opcional)
- Malhas com Mobilidade **Static** podem ter a luz indireta assada: **Compilar > Build Lighting Only**. [Mostrar onde](show:Build>Build Lighting Only)
- A qualidade fica em **Compilar > Lighting Quality** (Preview / Production).
- O bake roda com um cartão no canto inferior direito e pode ser cancelado nele.
--- en
```diagram compare
 | Looks like | Good for
Directional | the sun | day, outdoors
Point | a bulb | lamps, torches
Spot | a flashlight | spotlights, headlights
Rect | a window, a panel | interiors
Sky | the whole sky | ambient light
```
## Add a light
- **Actor > Add** has Directional (the sun), Point, Spot, Rect and Sky Light. [Add a Point Light](add:Point Light) [Show me where](show:Actor>Add)
- Intensity uses physical units (lux, candela); the Details panel shows each field.

## Baked light (optional)
- Meshes with Mobility **Static** can have their indirect light baked: **Build > Build Lighting Only**. [Show me where](show:Build>Build Lighting Only)
- The quality is in **Build > Lighting Quality** (Preview / Production).
- The bake runs with a card at the bottom right, where it can be cancelled.
