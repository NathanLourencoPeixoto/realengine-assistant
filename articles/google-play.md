id: google-play
kind: howto
title: Publicar na Google Play (AAB) | Publish on Google Play (AAB)
keys: google play, play store, publicar celular, publish android, aab, android app bundle, bundle, play console, chave de upload, upload key, keystore, assinar, signing, version code, versao, sdk alvo, target sdk, api 36, 16 kb, asset pack, 200 mb, icone da loja, store icon, feature graphic, grafico de destaque, politica de privacidade, privacy policy, loja, store listing
--- pt
```diagram steps
Configurações do Projeto > Android: nome do pacote seu (com.suaempresa.jogo) | Criar Chave de Upload (uma vez; guarde uma cópia) | Compilar > Empacotar para Google Play (AAB) | Play Console > Criar app > envie o .aab | Página da loja: as imagens de <jogo>_GooglePlay
```
## O que sai
- **`<jogo>.aab`**: o Android App Bundle que o Play Console recebe, assinado com a sua **chave de upload**. A Google assina de novo para cada aparelho (Play App Signing).
- **`<jogo>.apk`**: o mesmo jogo para instalar e testar antes (`adb install`).
- **`<jogo>_GooglePlay/`**: o ícone de 512 px e o gráfico de destaque de 1024 x 500 (feito da imagem de carregamento do projeto) para a página da loja. As capturas de tela você tira do celular.

## O que a engine já cumpre
- SDK alvo **36** (Android 16), exigido desde 31/08/2026; mínimo Android 11.
- 64 bits (arm64-v8a) e **páginas de 16 KB** (Android 15 em diante).
- Ícone adaptativo (a figura no círculo, sobre a cor *Fundo do Ícone*).
- Jogo com mais de 150 MB de arquivos: eles vão num **asset pack install-time**, porque a base do AAB tem limite de 200 MB. O jogo os lê do mesmo jeito.
- **Version Code** sobe sozinho depois de cada AAB, porque a loja recusa um número repetido.

## O checklist
Na mesma página das Configurações, cada item fica verde quando está certo: nome do pacote seu, chave de upload, ícone do jogo e política de privacidade (o Play Console pede o endereço para jogos online).

**Nunca perca a chave de upload** (`Build/Android/upload.keystore` e o `.pass` no projeto). Se perder, o suporte da Google pode trocar a chave, mas demora. Linha de comando: `realengine --open Level.rlevel --package-play <pasta>`. Veja também [Exportar para Android](article:android-export).
--- en
```diagram steps
Project Settings > Android: your own package name (com.yourcompany.game) | Create Upload Key (once; keep a copy) | Build > Package for Google Play (AAB) | Play Console > Create app > upload the .aab | Store listing: the pictures in <game>_GooglePlay
```
## What comes out
- **`<game>.aab`**: the Android App Bundle the Play Console takes, signed with your **upload key**. Google signs it again for each device (Play App Signing).
- **`<game>.apk`**: the same game to install and test first (`adb install`).
- **`<game>_GooglePlay/`**: the 512 px icon and the 1024 x 500 feature graphic (made from the project's loading picture) for the store listing. Take the screenshots on your phone.

## What the engine already meets
- Target SDK **36** (Android 16), required since 2026-08-31; minimum Android 11.
- 64-bit (arm64-v8a) and **16 KB pages** (Android 15 and later).
- Adaptive icon (the picture in the circle, over the *Icon Background* color).
- A game with more than 150 MB of files: they go in an **install-time asset pack**, because the bundle's base is limited to 200 MB. The game reads them the same way.
- **Version Code** goes up by itself after each bundle, because the store refuses a repeated number.

## The checklist
On the same Settings page, each item turns green when it is right: your own package name, the upload key, the game's icon and a privacy policy (the Play Console asks for its address for online games).

**Never lose the upload key** (`Build/Android/upload.keystore` and its `.pass` in the project). If you lose it, Google's support can replace it, but it takes time. Command line: `realengine --open Level.rlevel --package-play <folder>`. See also [Export to Android](article:android-export).
