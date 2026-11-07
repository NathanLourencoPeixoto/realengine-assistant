id: replication-pro
kind: concept
title: Replicação: RPCs e variáveis replicadas | Replication: RPCs and replicated variables
keys: replicacao, replication, rpc, run on server, multicast, owning client, variavel replicada, autoridade, authority, servidor, cliente, netcode, lag, perda de pacote
--- pt
```diagram compare
 | Quem chama | Onde roda
Run on Server | um cliente | o servidor
Multicast | o servidor | todos
Run on Owning Client | o servidor | o dono do ator
```
- Protocolo próprio sobre UDP com acks, canais confiáveis e não confiáveis e um emulador de lag e perda (para testar).
- Characters e corpos com física já sincronizam; outros atores: **Set Replicates**.
- **RPCs:** Run on Server (cliente pede), Multicast (servidor avisa todos), Run on Owning Client.
- **Variáveis replicadas** e **Has Authority** para decidir quem manda.
- Os clientes interpolam o movimento: fica liso mesmo com lag.
--- en
```diagram compare
 | Who calls | Where it runs
Run on Server | a client | the server
Multicast | the server | everyone
Run on Owning Client | the server | the actor's owner
```
- An own protocol over UDP with acks, reliable and unreliable channels and a lag and loss emulator (for testing).
- Characters and physics bodies sync already; other actors: **Set Replicates**.
- **RPCs:** Run on Server (a client asks), Multicast (the server tells everyone), Run on Owning Client.
- **Replicated variables** and **Has Authority** to decide who's in charge.
- Clients interpolate movement: smooth even with lag.
