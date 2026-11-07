id: multiplayer
kind: howto
title: Multiplayer (LAN e Steam) | Multiplayer (LAN and Steam)
keys: multiplayer, online, rede, coop, lan, steam, servidor, sessao, jogar com amigos, replicar, host, entrar
--- pt
```diagram steps
Create Session (quem hospeda) | Find Sessions | Join Session | Replicação: Set Replicates, RPCs
```
- Sessões: **Create Session**, **Find Sessions** e **Join Session** (LAN ou Steam).
- O que se move sozinho (Characters, física) já é replicado; o resto com **Set Replicates**, variáveis replicadas e RPCs (servidor, multicast, dono).
- Steam: ligue em Configurações do Projeto e ponha o `steam_api64.dll` do Steamworks SDK ao lado do `.rproject`. [Abrir as Configurações do Projeto](open:project)
--- en
```diagram steps
Create Session (the host) | Find Sessions | Join Session | Replication: Set Replicates, RPCs
```
- Sessions: **Create Session**, **Find Sessions** and **Join Session** (LAN or Steam).
- What moves by itself (Characters, physics) is replicated already; the rest with **Set Replicates**, replicated variables and RPCs (server, multicast, owner).
- Steam: turn it on in Project Settings and put the Steamworks SDK's `steam_api64.dll` next to the `.rproject`. [Open Project Settings](open:project)
