id: editor-utilities
kind: howto
title: Ferramentas próprias do editor | Your own editor tools
keys: utilitario do editor, editor utility, automatizar, ferramenta, ferramentas, script do editor, mudar varios atores, blutility
--- pt
1. Crie um script (ou Blueprint) com o pai **EditorUtility**: Navegador > **Adicionar > Script > Utilitário do Editor**.
2. Cada evento dele vira um botão em **Ferramentas > Utilitários do Editor**. [Abrir](open:utilities)
3. O botão roda no nível do editor (fora do Play) e **Ctrl+Z** desfaz.

```real
class EUW_Raise extends EditorUtility
    event RaiseSelected()
        for i in 0..GetSelectedActorCount()
            var a = GetSelectedActor(i)
            a.AddActorWorldOffset(Vector(0, 0, 50))
```
--- en
1. Make a script (or Blueprint) whose parent is **EditorUtility**: Browser > **Add > Script > Editor Utility**.
2. Each of its events becomes a button in **Tools > Editor Utilities**. [Open it](open:utilities)
3. The button runs on the editor's level (outside Play) and **Ctrl+Z** undoes it.

```real
class EUW_Raise extends EditorUtility
    event RaiseSelected()
        for i in 0..GetSelectedActorCount()
            var a = GetSelectedActor(i)
            a.AddActorWorldOffset(Vector(0, 0, 50))
```
