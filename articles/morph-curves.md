id: morph-curves
kind: howto
title: Curvas de morph: animar expressões na sequência | Morph curves: animate expressions in the sequence
keys: curva de morph, morph curve, curvas de morph, morph curves, curva na animacao, animation curve, animar morph target, animate morph target, animar expressao, animate expression, animar blend shape, shape key animada, gltf weights, canal weights, facial animation, animacao facial, sorriso animado, piscar animado, anim blueprint morph, set morph target anim blueprint
--- pt
Como as **curvas** das animações da Unreal: o peso de um morph target muda ao longo da **sequência** e acompanha a pose.
1. **Importe** um glTF com a animação dos pesos (o canal `weights`, que o Blender exporta das Shape Keys animadas): a sequência ganha uma curva por morph target, pelo nome. Uma malha sem armature vira um Skeletal Mesh de um osso que já toca a sequência.
2. Ou **crie** na sequência: abra-a, seção **Curvas** > **Adicionar Curva** (os morph targets da malha). Mova o cursor do tempo e mude o valor: vira uma **chave** ali; clique direito numa bolinha apaga a chave.
3. Jogando, as curvas se misturam junto com as poses (blend spaces, transições, montagens) e **mandam no peso** do morph target. Como na Unreal, a curva vence o **Set Morph Target**; um morph target sem curva segue o Set Morph Target ou o Details.
4. No **Anim Blueprint**, Set Morph Target e Get Morph Target funcionam no Event Graph (sem Target, a malha dele): para dirigir um peso por variável (piscar aleatório, boca pelo volume da voz).

```diagram steps
Sequência > Curvas | Adicionar Curva (Smile) | cursor em 0,5 s, valor 1 | Play: o rosto sorri junto com a animação
```
Custo: cerca de 9 ns por curva e quadro (uma busca nas chaves); sem curvas, nada.
--- en
Like Unreal's animation **curves**: a morph target's weight changes along the **sequence** and follows the pose.
1. **Import** a glTF with the weights' animation (the `weights` channel, which Blender exports from animated Shape Keys): the sequence gets a curve per morph target, by name. A mesh without an armature becomes a one-bone Skeletal Mesh already playing the sequence.
2. Or **create** it in the sequence: open it, **Curves** section > **Add Curve** (the mesh's morph targets). Move the time cursor and change the value: it becomes a **key** there; a right click on a dot deletes the key.
3. While playing, the curves blend along with the poses (blend spaces, transitions, montages) and **drive the weight** of the morph target. As in Unreal, the curve wins over **Set Morph Target**; a morph target with no curve follows Set Morph Target or the Details.
4. In an **Anim Blueprint**, Set Morph Target and Get Morph Target work in the Event Graph (no Target: its mesh): to drive a weight from a variable (a random blink, the mouth by the voice's volume).

```diagram steps
Sequence > Curves | Add Curve (Smile) | cursor at 0.5 s, value 1 | Play: the face smiles with the animation
```
Cost: about 9 ns per curve and frame (a search in the keys); without curves, nothing.
