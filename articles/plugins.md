id: plugins
kind: recipe
title: Plugins: nós e ferramentas em código nativo | Plugins: nodes and tools in native code
keys: plugin, plugins, criar plugin, make a plugin, new plugin, novo plugin, dll, extensao, extension, modulo nativo, native module, codigo nativo, native code, c plugin, blueprint function library, biblioteca de funcoes, nos novos, new nodes, edit plugins, ativar plugin, enable plugin, desativar plugin, disable plugin, plugin.json, sdk
--- pt
```diagram steps
Editar > Plugins > Novo Plugin...: escreva o nome (ex.: MeuPlugin)
Abra Plugins/MeuPlugin/Source/MeuPlugin.c e escreva as funções
Rode build.bat (precisa do Visual Studio com C++), reinicie o editor
Os nós aparecem na categoria Plugins dos Blueprints e nos scripts
```
Um **plugin** é uma pasta com um `plugin.json` e uma DLL. Fica em `<projeto>/Plugins/<Nome>`, ou em `Plugins/` ao lado da engine. Na abertura, a engine carrega os plugins ativos, e cada um registra o que traz pelo `plugin_api.h`, um cabeçalho C só:
- **Nós de Blueprint:** **puros** (um valor, sem pinos de execução) ou **chamáveis** (Exec de entrada e saída), com até 8 entradas e 4 saídas de float, int, bool, vector, rotator ou color. O mesmo nó vira função nos scripts: "Smooth Step" é `SmoothStep(...)` em Real, C#, Python e C.
- **Tick:** uma função chamada a cada quadro, no editor e no jogo.
- **Menu:** itens em Ferramentas > Plugins (só no editor).
**Editar > Plugins** lista todos, com a caixa para ativar, a versão, o autor, o estado (carregado, desativado, com erro) e os nós de cada um. Uma mudança vale na próxima abertura, como na Unreal; ela fica em `Config/Plugins.ini`.
**Segurança:** se uma função do plugin travar (acesso inválido), o plugin é desligado e o editor continua.
**Empacotar o jogo** leva os plugins carregados para `Plugins/` do pacote.
O **Example Plugin** (ao lado da engine, desligado de fábrica) mostra tudo isso e traz o código-fonte em `Plugins/ExamplePlugin/Source`.
```c
#include "plugin_api.h"
static void dobro(const RePluginValue* in, RePluginValue* out, void* user) {
    out[0].v[0] = in[0].v[0] * 2.0f;
}
RE_PLUGIN_EXPORT int re_plugin_init(const RePluginApi* api) {
    api->add_function(api->plugin, "Double It", "Math", "O valor vezes 2.",
                      "i:float:Value,o:float:Return Value", true, dobro, 0);
    return 0;
}
```
--- en
```diagram steps
Edit > Plugins > New Plugin...: type the name (e.g. MyPlugin)
Open Plugins/MyPlugin/Source/MyPlugin.c and write the functions
Run build.bat (needs Visual Studio with C++), restart the editor
The nodes show up in the Blueprints' Plugins category and in the scripts
```
A **plugin** is a folder with a `plugin.json` and a DLL. It lives in `<project>/Plugins/<Name>`, or in `Plugins/` next to the engine. At startup the engine loads the enabled plugins, and each registers what it brings through `plugin_api.h`, a single C header:
- **Blueprint nodes:** **pure** (a value, no execution pins) or **callable** (Exec in and out), with up to 8 inputs and 4 outputs of float, int, bool, vector, rotator or color. The same node becomes a function in the scripts: "Smooth Step" is `SmoothStep(...)` in Real, C#, Python and C.
- **Tick:** a function called every frame, in the editor and in the game.
- **Menu:** items under Tools > Plugins (editor only).
**Edit > Plugins** lists them all, with the box to enable each, its version, author, state (loaded, disabled, failed) and nodes. A change counts at the next start, as in Unreal; it is kept in `Config/Plugins.ini`.
**Safety:** if a plugin's function crashes (an invalid access), the plugin is turned off and the editor goes on.
**Package Game** takes the loaded plugins into the package's `Plugins/`.
The **Example Plugin** (next to the engine, off by default) shows all of this and has its source code in `Plugins/ExamplePlugin/Source`.
```c
#include "plugin_api.h"
static void twice(const RePluginValue* in, RePluginValue* out, void* user) {
    out[0].v[0] = in[0].v[0] * 2.0f;
}
RE_PLUGIN_EXPORT int re_plugin_init(const RePluginApi* api) {
    api->add_function(api->plugin, "Double It", "Math", "The value times 2.",
                      "i:float:Value,o:float:Return Value", true, twice, 0);
    return 0;
}
```
