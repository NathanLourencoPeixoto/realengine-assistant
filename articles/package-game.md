id: package-game
kind: howto
title: Empacotar o jogo | Package the game
keys: package the game, package game, packaging, empacotar o jogo, shipping, content.rpak, pacote unico, single file, arquivo unico, empacotar, exportar, exe, executavel, distribuir, publicar, build final, package, ship, jogo pronto, steam, plataforma, platform, escolher plataforma
--- pt
```diagram steps
Compilar > Empacotar Jogo | Escolher a pasta de saída | Package Game | Cartão no canto (Cancelar) | A pasta abre com o .exe
```
1. **Compilar > Empacotar Jogo...** abre a janela com todas as opções (nome, ícone, versão, resolução, tela cheia). [Abrir](open:package) [Mostrar onde](show:Build>Package Game...)
2. Escolha a **pasta de saída** e clique em **Package Game**.
3. A cópia roda em segundo plano (um cartão no canto inferior direito, com Cancelar); a pasta abre no Explorer quando termina.

O resultado é uma pasta com o `.exe` do jogo, o nível, a luz assada e os assets usados.

**Shipping:** marcado, o pacote sai sem o Debug Viewer e com todo o conteúdo num arquivo só, `Content.rpak` (comprimido e conferido ao abrir: um arquivo alterado não abre). Fica mais limpo para distribuir e o jogo lê tudo de lá.
- **Plataforma:** no topo da janela **Empacotar Jogo** escolha **Windows (64 bits)**, **Android (APK)** ou **Android (Google Play)**. A janela já abre com as configurações do projeto (e a plataforma usada da última vez; um projeto com nome de pacote Android ou controles de toque abre no Android). No Android aparecem o nome do pacote, a orientação, a versão, a qualidade e os controles de toque; **Mais Configurações do Android...** abre o resto.

--- en
```diagram steps
Build > Package Game | Pick the output folder | Package Game | A card at the corner (Cancel) | The folder opens with the .exe
```
1. **Build > Package Game...** opens the window with every option (name, icon, version, resolution, fullscreen). [Open it](open:package) [Show me where](show:Build>Package Game...)
2. Pick the **output folder** and click **Package Game**.
3. The copy runs in the background (a card at the bottom right, with Cancel); the folder opens in Explorer when it's done.

The result is a folder with the game's `.exe`, the level, its baked light and the assets used.

**Shipping:** checked, the package comes without the Debug Viewer and with all its content in a single file, `Content.rpak` (compressed and checked when it opens: a tampered file won't open). Cleaner to distribute, and the game reads everything from it.
- **Platform:** at the top of the **Package Game** window choose **Windows (64-bit)**, **Android (APK)** or **Android (Google Play)**. The window opens with the project's settings (and the platform used last time; a project with an Android package name or touch controls opens on Android). On Android it shows the package name, orientation, version, quality and touch controls; **More Android Settings...** opens the rest.
