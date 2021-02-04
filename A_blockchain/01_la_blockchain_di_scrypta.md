# La blockchain di Scrypta

Come abbiamo accennato nella prefazione [Scrypta](https://scryptachain.org) è una blockchain derivante da [PIVX](https://pivx.org/) che è, appunto un cugino non troppo lontano di [Bitcoin](https://bitcoin.org/it/). Questo significa che possiamo aspettarci da Scrypta (quasi) tutto quello che possiamo aspettarci da Bitcoin.

Le differenze sostanziali stanno nel metodo di consenso adottato (Proof of Work vs Proof of Stake), la velocità dei blocchi e la dimensione di un parametro fondamentale, che permette la scrittura di dati non relativi alle transazioni chiamato `OP_RETURN`.

Da un punto di vista di sviluppo in realtà sono molto simili e permettono di inviare transazioni per mezzo di `indirizzi` cui fanno capo una o più `utxo`, prendendo la definizione direttamente dalla wiki di Bitcoin:

> UTXO stands for Unspent Transaction (TX) Output. Every on-chain bitcoin transaction sends bitcoin to one or more addresses, from at least zero (in case of a coinbase transcation) addresses. A bitcoin wallet balance is actually the sum of the UTXOs controlled by the wallet's private keys.

Stringando molto i concetti più complessi (mi perdonino i puristi) possiamo sintetizzare che la blockchain non è altro che un insieme di `utxo` spesi all'interno di transazioni inserite all'interno di blocchi (se ritenute valide dal network). Una volta inserite all'interno di blocchi queste transazioni non possono essere più modificate (escludiamo attacchi di qualsiasi natura in questo momento) perchè mantenute all'interno di un network decentralizzato di nodi che in maniera ridondante mantengono il contenuto inalterato.

La riflessione spontanea riguarda chiaramente la generazione di questi `utxo`, ovvero da dove arrivano e come vengono generati e resi disponibili. Nel caso di Scrypta questi vengono generati ogni `minuto` circa ogni qualvolta che un nuovo blocco viene immesso dalla rete da uno degli stakers e che quindi li possono cedere o impiegare nelle transazioni per scrivere dati.

## Stakers e Masternodes

Come abbiamo anticipato poco prima ogni minuto circa viene emesso un nuovo blocco della blockchain, il meccanismo di consenso prevede che uno a caso degli staker (ovvero dei full node online che abbia una quantità di coin in staking) venga deputato alla creazione di un nuovo blocco e che quest'ultimo scelga uno dei masternode (a rotazione) per dividere la produzione di coin del blocco.

Lo staker quindi creerà il blocco e lo invierà alla rete per la validazione. Se il blocco è valido allora viene inserito in blockchain e le transazioni al suo interno vengono confermate. Se per qualche motivo invece il blocco risulta invalido allora questo verrà rifiutato dal network e verrà scelto un nuovo staker.