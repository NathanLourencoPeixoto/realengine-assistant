id: sound
kind: howto
title: Sons e música | Sound and music
keys: som, audio, musica, efeito sonoro, wav, ogg, ambiente, tocar som, sound cue, volume, 3d, surround
--- pt
1. Importe o **.wav** ou **.ogg** (arraste para o Navegador de Conteúdo): vira uma **Sound Wave**.
2. Som de ambiente no nível: **Ator > Adicionar > Ambient Sound** e escolha o som no Details. [Adicionar](add:AmbientSound)
3. Por código ou Blueprint: `PlaySound2D("Nome", 1.0, 1.0, 0.0)` (sem posição) ou `PlaySoundAtLocation(...)` (no espaço 3D).

Também há Sound Cues, atenuação, volumes de reverb, mixagem e surround 5.1/7.1.
--- en
1. Import the **.wav** or **.ogg** (drag it into the Content Browser): it becomes a **Sound Wave**.
2. An ambient sound in the level: **Actor > Add > Ambient Sound** and pick the sound in Details. [Add one](add:AmbientSound)
3. From code or a Blueprint: `PlaySound2D("Name", 1.0, 1.0, 0.0)` (no position) or `PlaySoundAtLocation(...)` (in 3D).

There are Sound Cues, attenuation, reverb volumes, mixing and 5.1/7.1 surround too.
