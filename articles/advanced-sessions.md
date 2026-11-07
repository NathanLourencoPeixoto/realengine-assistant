id: advanced-sessions
kind: recipe
title: Sessões avançadas: senha, filtros, banir | Advanced sessions: password, filters, bans
keys: advanced sessions, advanced session, sessoes avancadas, sessao avancada, ban player, banir jogador, unban, banned, banido, kick player, senha, password, filtro de sessao, search filter, propriedade da sessao, session property, extra settings, regiao, region, mapa, modo de jogo, game mode, private slots, vagas privadas, banir, ban, kick, trancar sessao, lock, join in progress, start session, end session, update session, convite, invite, amigo, friend, lobby, servidor dedicado, ping, matchmaking
--- pt
Como o plugin **Advanced Sessions** da Unreal: tudo da sessão no seu controle (categoria **Online|Advanced Sessions**).

```diagram steps
Set Session Property (região, nível...) | Create Advanced Session (vagas, senha, mapa, modo) | Add Session Search Filter + Find Sessions Advanced | Get Session Details | Join Session Advanced (senha)
```
- **Create Advanced Session**: vagas públicas e **Private Slots** (só para quem vem por convite, amigo ou endereço), LAN ou Steam, **Visibility** (0 pública, 1 só amigos, 2 só convite), **Password**, **Allow Join In Progress**, **Allow Invites**, **Should Advertise** (desligado: a busca não acha), mapa e modo de jogo.
- **Set Session Property** guarda chaves suas (região, dificuldade, rodada). Antes de criar, entram na criação; com a sessão aberta, o host muda na hora e todos veem (**Event On Session Updated**).
- **Find Sessions Advanced**: tipo de servidor (0 todos, 1 listen, 2 dedicado), vagas mínimas, sem cheias, só vazias / só com gente, sem senha, sem partidas começadas, ping máximo, mesma versão. **Add Session Search Filter** compara uma propriedade (0 igual, 1 diferente, 2 menor, 3 menor ou igual, 4 maior, 5 maior ou igual, 6 contém); números comparam como números. Os resultados vêm do mais perto.
- **Get Session Details** lê cada resultado (nome, host, jogadores, vagas, ping, mapa, modo, dedicado, senha, começada).
- **Join Session Advanced** entra com a senha. Recusado (cheia, trancada, começou, senha errada, banido, outra versão): **Event On Join Session Complete** traz o motivo, e **Get Last Session Error** também.
- Durante a partida: **Start Session** / **End Session**, **Set Session Joinable** (trancar), **Update Session**, **Ban Player** / **Unban**, **Event On Join Refused** (no host).
- Steam: **Join Friend Session**, **Invite Friend To Session**, **Set Auto Accept Invites** + **Event On Session Invite Accepted**.

```blueprint
Event BeginPlay -> Set Session Property ( "region", "sa" ) -> Create Advanced Session ( "Minha Sala", 4, 1, true, 0, "1234", true, true, true, "Arena", "CTF" )
Event On Sessions Found -> Branch ( Count > 0 ) -> Join Session Advanced ( 0, "1234" )
```
```real
class Lobby extends Actor
    var searching = false

    event Host()
        SetSessionProperty("region", "sa")
        CreateAdvancedSession("Minha Sala", 4, 1, true, 0, "1234", true, true, true, "Arena", "CTF")

    event Search()
        ClearSessionSearchFilters()
        AddSessionSearchFilter("region", "sa", 0)
        FindSessionsAdvanced(true, 20, 0, 1, true, false, false, false, false, 150.0, true)
        searching = true

    event Tick(dt: float)
        if searching and not IsFindingSessions()
            searching = false
            if GetSessionCount() > 0
                JoinSessionAdvanced(0, "1234")
            else
                print("Nenhuma sala: {GetLastSessionError()}")
```
Veja também [Multiplayer](article:multiplayer).
--- en
Like Unreal's **Advanced Sessions** plugin: everything about the session in your hands (category **Online|Advanced Sessions**).

```diagram steps
Set Session Property (region, level...) | Create Advanced Session (slots, password, map, mode) | Add Session Search Filter + Find Sessions Advanced | Get Session Details | Join Session Advanced (password)
```
- **Create Advanced Session**: public slots and **Private Slots** (only for who comes by an invite, a friend or the address), LAN or Steam, **Visibility** (0 public, 1 friends only, 2 invite only), **Password**, **Allow Join In Progress**, **Allow Invites**, **Should Advertise** (off: the searches don't find it), map and game mode.
- **Set Session Property** keeps your own keys (region, difficulty, round). Before creating, they go into the session; while it runs, the host changes them at once and everyone sees it (**Event On Session Updated**).
- **Find Sessions Advanced**: server type (0 all, 1 listen, 2 dedicated), minimum open slots, no full ones, empty only / non empty only, no password, no started matches, max ping, same build. **Add Session Search Filter** compares a property (0 equal, 1 not equal, 2 less, 3 less or equal, 4 greater, 5 greater or equal, 6 contains); numbers compare as numbers. The results come nearest first.
- **Get Session Details** reads each result (name, host, players, slots, ping, map, mode, dedicated, password, started).
- **Join Session Advanced** joins with the password. Refused (full, locked, started, wrong password, banned, another build): **Event On Join Session Complete** brings the reason, and so does **Get Last Session Error**.
- During the match: **Start Session** / **End Session**, **Set Session Joinable** (lock), **Update Session**, **Ban Player** / **Unban**, **Event On Join Refused** (on the host).
- Steam: **Join Friend Session**, **Invite Friend To Session**, **Set Auto Accept Invites** + **Event On Session Invite Accepted**.

```blueprint
Event BeginPlay -> Set Session Property ( "region", "sa" ) -> Create Advanced Session ( "My Room", 4, 1, true, 0, "1234", true, true, true, "Arena", "CTF" )
Event On Sessions Found -> Branch ( Count > 0 ) -> Join Session Advanced ( 0, "1234" )
```
```real
class Lobby extends Actor
    var searching = false

    event Host()
        SetSessionProperty("region", "sa")
        CreateAdvancedSession("My Room", 4, 1, true, 0, "1234", true, true, true, "Arena", "CTF")

    event Search()
        ClearSessionSearchFilters()
        AddSessionSearchFilter("region", "sa", 0)
        FindSessionsAdvanced(true, 20, 0, 1, true, false, false, false, false, 150.0, true)
        searching = true

    event Tick(dt: float)
        if searching and not IsFindingSessions()
            searching = false
            if GetSessionCount() > 0
                JoinSessionAdvanced(0, "1234")
            else
                print("No rooms: {GetLastSessionError()}")
```
See also [Multiplayer](article:multiplayer).
