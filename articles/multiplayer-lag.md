id: multiplayer-lag
kind: recipe
title: Multiplayer sem lag: perda de pacote e tiros justos | Lag-free multiplayer: packet loss and fair shots
keys: lag, ping alto, high ping, packet loss, perda de pacote, travando online, online stutter, teleporte, rubber band, rubberbanding, interpolacao, interpolation, jitter, compensacao de lag, lag compensation, server rewind, tiro justo, hit registration, hitscan, acertar tiro, lag compensated trace, rede ruim, bad network, emulacao de rede, network emulation
--- pt
```diagram compare
| sem a engine | com a engine
pacote perdido com o ator parado | parado no lugar errado até 2 s | no lugar certo em ~1 ida e volta
atraso de desenho | fixo | cresce com a perda e o jitter, sem trancos
salto de extrapolação | pula | some em ~0,1 s
tiro sob lag | erra quem estava na mira | acerta onde o atirador viu
```
## Perda de pacote
O servidor guarda, para cada jogador, o último estado que ele **confirmou** ter recebido. Se um pacote se perde, o estado vai de novo depois de uma ida e volta. Com 20% de perda nos dois sentidos, todo ator fica no lugar certo em até ~0,5 s depois de parar; antes podia levar 2 s. Os estados também ficaram menores: 12 bytes parado e 18 andando, contra 21.

## Lag e jitter
O cliente desenha os outros um pouco no passado. Esse atraso cresce sozinho com a perda (um snapshot perdido é coberto pela interpolação) e com o jitter, e muda devagar. O relógio de desenho acelera ou freia uns poucos por cento em vez de pular. Quando chega um estado que contradiz a extrapolação, a diferença some em ~0,1 s em vez de dar um salto.

## Tiros justos (compensação de lag)
No servidor, o nó **Lag Compensated Trace** testa o tiro contra onde o atirador **viu** os outros jogadores: volta metade do ping dele mais o atraso de desenho, até 1 s. Os Characters são testados pela cápsula.
```blueprint
Event Fire -> Run on Server ( "ServerFire", Get Local Player Index )
Event ServerFire -> Lag Compensated Trace ( Start, End, Get RPC Sender, 0 ) -> Branch ( Hit ) True -> Destroy Actor ( Hit Actor )
```
Teste em rede ruim: Configurações do Projeto > Online > Emulação de Rede (latência, jitter, perda). Veja também [Multiplayer](article:multiplayer).
--- en
```diagram compare
| without the engine | with the engine
lost packet, actor stopped | stuck in the wrong place up to 2 s | in the right place in ~1 round trip
draw delay | fixed | grows with loss and jitter, no stutter
extrapolation jump | pops | fades in ~0.1 s
shot under lag | misses who was in the crosshair | hits where the shooter saw
```
## Packet loss
For each player, the server keeps the last state that player **confirmed** receiving. When a packet is lost, the state goes again after one round trip. With 20% loss both ways, every actor is in the right place within ~0.5 s of stopping; before it could take 2 s. States also got smaller: 12 bytes still and 18 walking, against 21.

## Lag and jitter
The client draws the others a little in the past. That delay grows by itself with loss (a lost snapshot is covered by interpolation) and with jitter, and it changes slowly. The draw clock speeds up or slows down a few percent instead of jumping. When a state arrives that contradicts the extrapolation, the difference fades in ~0.1 s instead of popping.

## Fair shots (lag compensation)
On the server, the **Lag Compensated Trace** node tests the shot against where the shooter **saw** the other players: it goes back half their ping plus their draw delay, up to 1 s. Characters are tested by their capsule.
```blueprint
Event Fire -> Run on Server ( "ServerFire", Get Local Player Index )
Event ServerFire -> Lag Compensated Trace ( Start, End, Get RPC Sender, 0 ) -> Branch ( Hit ) True -> Destroy Actor ( Hit Actor )
```
Test on a bad network: Project Settings > Online > Network Emulation (latency, jitter, loss). See also [Multiplayer](article:multiplayer).
