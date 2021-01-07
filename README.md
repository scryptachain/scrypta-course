# Corso per sviluppatori blockchain Scrypta

Scrypta sta preparando un corso di formazione per sviluppatori che permetterà a chiunque di iniziare a mettere le mani "in pasta" e sviluppare applicazioni decentralizzate più o meno complesse.

Il corso verrà sviluppato in due formati: uno puramente testuale ed uno video, commentato da uno sviluppatore che vi permettrà di seguire gli esempi più facilmente.

Se avete dubbi o volete migliorare questo corso siete liberi di aprire delle [issue](https://github.com/scryptachain/scrypta-development-course/issues), cercheremo di rispondere a tutte le domande e accoglieremo eventuali suggerimenti.

## Informazioni preliminari

Sebbene la [wiki](https://scrypta.wiki) sia il posto migliore per iniziare a dare uno sguardo al mondo Scrypta in generale è meglio fissare alcuni concetti di base all'inizio, così da porre le giuste basi analitiche a tutto lo sviluppo blockchain basato sulla tecnologia Scrypta.

1. Scrypta è una blockchain derivante direttamente da Bitcoin, in quanto fork di PIVX. Non aspettatevi quindi di avere a che fare con qualcosa di simile ad `Ethereum`, sebbene si possano raggiungere gli stessi risultati, le dinamiche di base sono diametralmente diverse.

2. Gli Smart Contracts (sebbene come vedremo non siano fondamentali per lo sviluppo di un'applicazione decentralizzata) sono comunque presenti ed il linguaggio di programmazione è `Javascript`, anche qui non aspettatevi di vedere `Solidity` come in `Ethereum`.

3. I due grandi motori dell'ambiente di sviluppo Scrypta sono `@scrypta/core` e `IdaNode`, realizzati con `Javascript` il primo e `TypeScript` il secondo. Conoscere `Javascript` è quindi fondamentale, il corso darà per scontato che abbiate delle basi in tal senso, che sappiate utilizzare `npm` e che riusciate a creare degli script. Se così non fosse vi preghiamo di ritornare su questo corso dopo aver dato quanto meno una lettura ad un corso di base, noi consigliamo [questo](https://www.html.it/guide/guida-javascript-di-base/).

4. Cercheremo invece di non dare per scontato nulla che abbia a che fare con la crittografia, con le firme, con gli indirizzi etc. Se non avete mai sentito parlare di blockchain state tranquilli, riusciremo a darvi un'infarinatura di base.

## Indice del corso

### A - Blockchain

01. [Come è fatta la blockchain di Scrypta](./A_blockchain/01_come_è_fatta_la_blockchain_di_scrypta.md)
02. Tipologie di nodi e loro utilizzi
03. Account blockchain, identità e transazioni
04. Block explorer ed analisi dei dati
05. I wallet di Scrypta

### B - Strumenti di sviluppo

06. IdaNode, come installarlo in locale
07. Core, la libreria Javascript
08. Interagire con l'IdaNode attraverso Postman
09. Interagire con l'IdaNode attraverso Core

### C - Interagire con la blockchain

10. Creiamo il nostro primo wallet blockchain
11. Inseriamo il nostro primo dato in blockchain
12. Tecniche di Progressive Data Management
13. Importanza delle firme blockchain
14. Panoramica sugli account multisignature

### D - Planum, il layer di tokenizzazione

15. Panoramica sul mondo dei token
16. Approfondimento sulle sidechain
17. Tipologie di sidechain e token
18. Come creare una nuova sidechain
19. Come interagire con la sidechain
20. Tools e software di supporto

### E - Smart Contracts

21. Panoramica generale
22. Configurazione ambiente di sviluppo
23. Scrittura e pubblicazione dello smart contract
24. Interazione attraverso Core
25. Interazione attraverso IdaNode
26. Mantenere online uno smart contract

### F - Creiamo una dApp

27. Strutturazione progetto frontend
28. Creazione semplice Smart Contract
29. Impostazione dinamiche di login
30. Interazione con lo Smart Contract
31. Pubblicazione della dApp

### G - Conclusioni

32. Identità digitale decentralizzata
33. dApp sviluppate da Scrypta Foundation
34. Contribuire al progetto Scrypta
