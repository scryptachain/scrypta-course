# Block explorer ed analisi dei dati

La cosa più importante da capire è come i dati sono inseriti all'interno della blockchain e come possiamo effettivamente andare a leggerli.
Per farlo abbiamo bisogno dei cosiddetti `block explorer` che ci permettono di capire blocco dopo blocco come le informazioni vengono mantenute.

Scrypta ha vari block explorer e sta a voi la scelta nell'utilizzo di uno o l'altro, in base alle vostre preferenze. 
L'unico mantenuto attivamente da Scrypta Foundation è però il `BlockBook`, forkato direttamente da Trezor.

Ecco l'elenco dei block explorer:

- BlockBook: https://bb.scryptachain.org (un block explorer generico)

- Explorer Staking: https://explorer.scryptachain.org (contenente più informazioni riguardo lo staking etc)

- Proof: https://proof.scryptachain.org (contenente unicamente i dati scritti in blockchain)

- IdaNode: https://scrypta.wiki/it/#/idanode/block-explorer (le chiamate API specifiche esposte dall'IdANode)

Analizziamo quindi il Blockbook così da vedere come è composto.

## Pagina di stato

Appena si entra all'interno dell'explorer vedremo la pagina di stato contenente le informazioni riguardanti l'applicativo in GO e la blockchain. Vedremo anche l'ultimo blocco disponibile, le transazioni in mempool e lo stato di sincronizzazione.

## Pagina dei blocchi

La [pagina dei blocchi](https://bb.scryptachain.org/blocks) contiene l'elenco sottoforma di tabella di tutti i blocchi disponibili. Qui è riportato l'hash del blocco, il numero di transazioni, la data e la dimensione.

## Pagina di un blocco

Prendendo ad esempio il blocco [1103803](https://bb.scryptachain.org/block/1103803) vedremo che la pagina è divisa in due parti principali: 

- **Summary**: che richiama le informazioni essenziali del blocco.

- **Transactions**: che richiama le informazioni per ogni singola transazione ovvero l'hash, gli input e gli output.

## Pagina di una transazione

Ogni [transazione](https://bb.scryptachain.org/tx/c9e93f4e2d587f0ae051cfb2d22a30a9510025edd8d1dc88c2dc181fd4b81588) ha una sua pagina specifica e anche qui vedremo la pagina divisa in tre parti principali:

- **Summary**: che richiama le informazioni essenziali della transazione ovvero il blocco in cui è stata inserita, il timestamp e la quantità di input / output.

- **Details**: che richiama le informazioni riguardo gli input e gli output.

- **Raw transaction**: che richiama le informazioni della transazione in formato grezzo, un po' come abbiamo visto precedentemente.

## Masternodes

La [pagina dei masternode](https://bb.scryptachain.org/masternodes) riporta tutte le informazioni riguardanti i masternode attivi ovvero gli indirizzi IP, gli indirizzi blockchain e lo status. Cliccando sui dettagli si andrà nella pagina relativa all'indirizzo del masternode.

## Pagina di un indirizzo

Ogni [indirizzo](https://bb.scryptachain.org/address/LWAoywbsgKLULtVpqBKeqwfYc9g9YntZYX) ha una sua pagina specifica che riporta il suo attuale bilancio, un piccolo riepilogo della quantità di LYRA che ha transato e la lista delle transazioni.