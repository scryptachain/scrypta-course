# Tipologie di nodi e loro utilizzo

Come ogni blockchain anche Scrypta si basa su un network decentralizzato di nodi. I nodi non sono nient'altro che computer (o server) che mettono a disposizione la loro potenza di calcolo e la loro connettività per creare ridondanza, backup e consenso.

Scrypta ha due diverse tipologie di nodi:

- *Full Node*: questi fanno da infrastruttura di base e mantengono principalmente i dati della blockchain ed il consenso. I full node a loro volta si possono "specializzare" in nodi di staking o masternode. Quest'ultimi nello specifico si occupano di produrre nuovi blocchi raggiungendo un consenso.

- *IdANode*: questi si interpongono tra gli utenti e la blockchain creando il layer applicativo di cui abbiamo bisogno per realizzare e scrivere le nostre applicazioni. Si occupano principalmente di leggere la blockchain e renderla disponibile in un database più performante (MongoDB) ed esporre delle API che possono servire all'utente o allo sviluppatore per interagire con la blockchain.

## Full Node

I full node utilizzano [questo](https://github.com/scryptachain/scrypta) software, scritto in C++ ed è proprio quello forkato da PIVX. Non ci soffermiamo molto su questa parte in quanto la [wiki](https://scrypta.wiki/it/#/wallet/fullnode) è parecchio esaustiva in tal senso e non ci serve ai fini della programmazione. La cosa *fondamentale* da capire è che, chiaramente, il full node è l'elemento di base che compone la blockchain.

### Installazione

Per installare un full node basta scaricare la versione che si preferisce da [GitHub](https://github.com/scryptachain/scrypta/releases/tag/2.0.1) ed avviarlo. Non dovrete installare alcuna dipendenza nemmeno su Linux.

Riassumiamo quindi tutta quanta la procedura di installazione:

```
wget https://github.com/scryptachain/scrypta/releases/download/2.0.1/lyra-2.0.1-linux-complete.zip
unzip lyra-2.0.1-linux-complete.zip
mv lyra-qt /usr/bin/lyra-qt
mv lyra-cli /usr/bin/lyra-cli
mv lyrad /usr/bin/lyrad
```

Per farlo partire potrete usare il comando `lyrad &` se volete attivare unicamente il daemon oppure `lyra-qt &` per avviare l'interfaccia grafica.

Per interagire con il full node abbiamo due possibilità:

- Command line interface (CLI): ovvero usando i [comandi disponibili](https://scrypta.wiki/it/#/wallet/fullnode#lista-dei-comandi) direttamente da terminale anteponendo `lyra-cli` al comando. Ad esempio il comando che ci restituisce lo stato del nodo è `lyra-cli`.

- Remote procedure call (RPC): ovvero facendo delle richieste HTTP al nodo. I comandi saranno gli stessi dell'interfaccia grafica mentre avremo bisogno di inviare i parametri di autenticazione scritti all'interno del file `lyra.conf` presente nella [directory](https://scrypta.wiki/it/#/wallet/fullnode#directory-dei-dati) principale.

Questo secondo metodo è quello più comune per gli sviluppatori e possiamo richiamarlo anche usando `@scrypta/core`, vedremo più avanti come nello specifico.

## IdANode

Gli IdANode utilizzano invece [questo](https://github.com/scryptachain/scrypta-idanodejs) software, scritto in NodeJS ed è sviluppato interamente da Scrypta Foundation. Per funzionare ha bisogno che nella stessa macchina ci sia installato *anche* un full-node in quanto le informazioni vengono prese sempre e comunque dalla blockchain.

Questo software è in continua evoluzione ed è importante sapere come installarlo e quali sono le sue API. Invitiamo comunque a tenere sott'occhio [questa](https://scrypta.wiki/it/#/idanode/inizio) parte della wiki in quanto faremo parecchi riferimenti.

Il task principale che esegue l'IdaNode è il `daemon` che potrete vedere in azione non appena il nodo viene avviato e non fa altro che, appunto, leggere la blockchain dal blocco 0 all'ultimo blocco disponibile. Una volta arrivato all'ultimo blocco si "metterà in ascolto" della `mempool` per la validazione pressocchè istantea dei dati. 

Il network infatti sincronizza lo stato ogni `500ms` ed è grazie a questa sincronizzazione che le transazioni all'interno della blockchain sono immediatamente disponibili anche se non vengono inserite in un blocco.

L'utilizzo della `mempool`, anche se in altre blockchain (tipo Bitcoin) non è così, è da considerarsi sicuro grazie al fatto che i Masternode tegnono conto di tutte le `utxo` e che non permettono a nessuno di effettuare un double-spending.

### Installazione

Per installare un IdaNode abbiamo appunto bisogno principalmente di NodeJS, di un full node e di MongoDB. Questi tre componenti vengono installati automaticamente dallo script [`install.sh`](https://github.com/scryptachain/scrypta-idanodejs/blob/master/scripts/install.sh) presente nella cartella principale.

Andiamo a mettere le mani nel terminale ed iniziamo a sporcarci un po' le mani!

```
git clone https://github.com/scryptachain/scrypta-idanodejs
cd scrypta-idanodejs
bash scripts/install.sh
```

Alla fine di questa procedura il nodo sarà già attivo e potremo farlo partire con `npm start`.

Per utilizzare l'IdaNode abbiamo necessariamente bisogno di usare `Postman` o `@scrypta/core` in quanto non è presente una `cli` come per il full node.