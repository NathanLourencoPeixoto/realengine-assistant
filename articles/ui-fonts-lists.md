id: ui-fonts-lists
kind: howto
title: Fontes, Rich Text e listas na UI | Fonts, Rich Text and lists in the UI
keys: fonte, fontes, font, fonts, ttf, otf, fonte propria, custom font, minha fonte, negrito, bold, italico, italic, contorno, outline, texto com contorno, rich text, rich text block, texto rico, texto colorido, cores no texto, palavra colorida, colored word, tag b, tag color, list view, tile view, lista, lista de itens, list of items, lista de missoes, quest list, inventario em lista, grade de itens, tiles, rolagem, scroll list, mil itens, thousands of items, virtualizada, virtualized, OnItemClicked, item selecionado, selected item, msdf
--- pt
```diagram steps
Ponha o .ttf/.otf em Content/Fonts (e os da família: -Bold, -Italic)
No Designer, Font: arraste o arquivo; Negrito e Itálico usam os da família
Rich Text Block: <b>, <i>, <color=#FFB020>, <size=32>, <outline>
List View / Tile View: itens com | entre eles ou Set Text no jogo
```
A UI do jogo (os Widget Blueprints) usa fontes do projeto, texto com marcações e listas de qualquer tamanho.
- **Fontes:** ponha o arquivo **.ttf** ou **.otf** em `Content/Fonts/` e, nos Details de um Text, Button, Rich Text ou lista, arraste-o para **Font** (vazio: a fonte da engine). A letra fica nítida em qualquer tamanho e escala de tela: os glifos são gerados no tamanho em que aparecem.
- **Negrito e itálico de verdade:** quando a família está ao lado (`Nome-Bold.ttf`, `Nome-Italic.ttf`, `Nome-BoldItalic.ttf`, ou os `nomeb`/`nomei`/`nomez` do Windows), **Bold** e **Italic** usam esses arquivos; sem eles, a engine engrossa e inclina a regular.
- **Outline:** um contorno em px (na tela de 1080p) com a sua cor, para ler texto sobre o cenário.
- **Rich Text Block** (Paleta > Common): o texto aceita `<b>negrito</b>`, `<i>itálico</i>`, `<color=#FF6020>cor</color>` (hexadecimal, alfa opcional), `<size=36>tamanho</size>` e `<outline>contorno</outline>`, que podem se aninhar; quebra por palavra com **Auto Wrap Text**.
- **List View e Tile View** (Paleta > Lists): os itens são o texto, com `|` entre eles. No jogo, **Set Text (Widget)** troca a lista inteira (junte um array com **Join String Array** e `|`): mil ou dez mil itens custam o mesmo, porque só as linhas visíveis são desenhadas. A roda do mouse rola; um clique seleciona e roda **OnItemClicked_<nome>** e **OnSelectionChanged_<nome>**. **Get Value** devolve o índice escolhido (-1: nenhum) e **Get Text** o item; **Set Value** escolhe. O Tile View tem **Columns**.
- **Custo** (RTX 3060): o teste da UI com Rich Text, três fontes e uma lista de 1000 itens desenha em ~0,065 ms (9 linhas desenhadas), 440 fps.
```blueprint
Event BeginPlay -> Set Text (Widget) ( Widget = "Quests", In Text = Join String Array ( Source Array = QuestNames, Separator = "|" ) )
Event OnItemClicked_Quests -> Print String ( Get Text (Widget) ( Widget = "Quests" ) )
```
--- en
```diagram steps
Put the .ttf/.otf in Content/Fonts (and its family's: -Bold, -Italic)
In the Designer, Font: drag the file; Bold and Italic use the family's
Rich Text Block: <b>, <i>, <color=#FFB020>, <size=32>, <outline>
List View / Tile View: items with | between them, or Set Text in the game
```
The game's UI (Widget Blueprints) uses the project's fonts, marked-up text and lists of any size.
- **Fonts:** put the **.ttf** or **.otf** file in `Content/Fonts/` and, in the Details of a Text, Button, Rich Text or list, drag it to **Font** (empty: the engine's font). The letters stay sharp at any size and screen scale: the glyphs are made at the size they show.
- **Real bold and italic:** when the family is next to it (`Name-Bold.ttf`, `Name-Italic.ttf`, `Name-BoldItalic.ttf`, or Windows' `nameb`/`namei`/`namez`), **Bold** and **Italic** use those files; without them, the engine thickens and slants the regular one.
- **Outline:** an outline in px (on a 1080p screen) in its color, to read text over the scenery.
- **Rich Text Block** (Palette > Common): the text takes `<b>bold</b>`, `<i>italic</i>`, `<color=#FF6020>color</color>` (hexadecimal, optional alpha), `<size=36>size</size>` and `<outline>outline</outline>`, which can nest; it breaks by word with **Auto Wrap Text**.
- **List View and Tile View** (Palette > Lists): the items are the text, with `|` between them. In the game, **Set Text (Widget)** replaces the whole list (join an array with **Join String Array** and `|`): a thousand or ten thousand items cost the same, because only the visible rows are drawn. The mouse wheel scrolls; a click selects and runs **OnItemClicked_<name>** and **OnSelectionChanged_<name>**. **Get Value** returns the chosen index (-1: none) and **Get Text** the item; **Set Value** chooses. The Tile View has **Columns**.
- **Cost** (RTX 3060): the UI test with Rich Text, three fonts and a 1000-item list draws in ~0.065 ms (9 rows drawn), 440 fps.
```blueprint
Event BeginPlay -> Set Text (Widget) ( Widget = "Quests", In Text = Join String Array ( Source Array = QuestNames, Separator = "|" ) )
Event OnItemClicked_Quests -> Print String ( Get Text (Widget) ( Widget = "Quests" ) )
```
