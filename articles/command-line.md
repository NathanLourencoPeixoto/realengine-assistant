id: command-line
kind: concept
title: Linha de comando e testes automáticos | Command line and automated tests
keys: linha de comando, argumentos, command line, cli, bench, teste automatico, ctest, realengine_background, validacao vulkan, screenshot, --shot, headless
--- pt
- `realengine.exe --project <arquivo.rproject>` abre um projeto; `--new-project <pasta> --template N` cria.
- `--bench N` mede N segundos e imprime FPS, CPU, GPU e os passes; `--shot arquivo.png` tira uma foto.
- `--validation` liga a camada de validação do Vulkan.
- `--upscaler tsr|fsr|dlss|xess` e `--upscale-mode 0-5` trocam o upscaler e o modo só nesta execução (medidas).
- `REALENGINE_BACKGROUND=1`: as janelas abrem fora da tela (testes sem atrapalhar).
- `REALENGINE_JIT=0` desliga o código nativo; `REALENGINE_ASSISTANT_URL` troca a base deste assistente.
- A suíte: `ctest --test-dir build -C Release`.
--- en
- `realengine.exe --project <file.rproject>` opens a project; `--new-project <folder> --template N` makes one.
- `--bench N` measures N seconds and prints FPS, CPU, GPU and the passes; `--shot file.png` takes a picture.
- `--validation` turns on Vulkan's validation layer.
- `--upscaler tsr|fsr|dlss|xess` and `--upscale-mode 0-5` swap the upscaler and the mode for this run only (measures).
- `REALENGINE_BACKGROUND=1`: the windows open off-screen (tests without getting in the way).
- `REALENGINE_JIT=0` turns the native code off; `REALENGINE_ASSISTANT_URL` swaps this assistant's base.
- The suite: `ctest --test-dir build -C Release`.
