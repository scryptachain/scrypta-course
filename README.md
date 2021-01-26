# Corso per sviluppatori blockchain Scrypta

Benvenuto nel corso di formazione per sviluppatori blockchain che tu permetterà di iniziare a mettere le mani "in pasta" e sviluppare applicazioni decentralizzate più o meno complesse.

Il corso verrà sviluppato in due formati: uno puramente testuale ed uno video, commentato da uno sviluppatore che ti permettrà di seguire gli esempi più facilmente.

Se avete dubbi o volete migliorare questo corso siete liberi di aprire delle [issue](https://github.com/scryptachain/scrypta-development-course/issues), cercheremo di rispondere a tutte le domande e accoglieremo eventuali suggerimenti.

## Informazioni preliminari

Sebbene la [wiki](https://scrypta.wiki) sia il posto migliore per iniziare a dare uno sguardo al mondo Scrypta in generale è meglio fissare alcuni concetti di base all'inizio, così da porre le giuste basi analitiche a tutto lo sviluppo blockchain basato sulla tecnologia Scrypta.

1. Scrypta è una blockchain derivante direttamente da Bitcoin, in quanto fork di [PIVX](https://pivx.org/). Non aspettatevi quindi di avere a che fare con qualcosa di simile ad `Ethereum`, sebbene si possano raggiungere gli stessi risultati, le dinamiche di base sono diametralmente diverse.

2. Gli Smart Contracts (sebbene come vedremo non siano fondamentali per lo sviluppo di un'applicazione decentralizzata) sono comunque presenti ed il linguaggio di programmazione è `Javascript`, anche qui non aspettatevi di vedere `Solidity` come in `Ethereum`.

3. I due grandi motori dell'ambiente di sviluppo Scrypta sono `@scrypta/core` e `IdaNode`, realizzati con `Javascript` il primo e `TypeScript` il secondo. Conoscere `Javascript` è quindi fondamentale, il corso darà per scontato che abbiate delle basi in tal senso, che sappiate utilizzare `npm` e che riusciate a creare degli script. Se così non fosse vi preghiamo di ritornare su questo corso dopo aver dato quanto meno una lettura ad un corso di base, noi consigliamo [questo](https://www.html.it/guide/guida-javascript-di-base/).

4. Cercheremo invece di non dare per scontato nulla che abbia a che fare con la crittografia, con le firme, con gli indirizzi etc. Se non avete mai sentito parlare di blockchain state tranquilli, riusciremo a darvi un'infarinatura di base.

## Indice del corso

### A - Blockchain

01. [La blockchain di Scrypta](./A_blockchain/01_come_è_fatta_la_blockchain_di_scrypta.md)
02. [Tipologie di nodi e loro utilizzi](./A_blockchain/02_tipologie_di_nodi_e_loro_utilizzi.md)
03. [Account blockchain, identità e transazioni](./A_blockchain/03_account_blockchain_identità_e_transazioni.md)
04. [Block explorer ed analisi dei dati](./A_blockchain/04_block_explorer_ed_analisi_dei_dati.md)
05. [I wallet di Scrypta](./A_blockchain/05_i_wallet_di_scrypta.md)

### B - Strumenti di sviluppo

06. [IdaNode, come installarlo in locale](./B_strumenti_di_sviluppo/06_idanode_come_installarlo_in_locale.md)
07. [Core, la libreria Javascript](./B_strumenti_di_sviluppo/07_core_la_libreria_javascript.md)
08. [Postman](./B_strumenti_di_sviluppo/08_postman.md)
09. [Interagre attraverso Core](./B_strumenti_di_sviluppo/09_interagire_attraverso_core.md)

### C - Interagire con la blockchain

10. [Creiamo il nostro primo wallet blockchain](./C_interagire_con_la_blockchain/10_creiamo_il_nostro_primo_wallet_blockchain.md)
11. [Inseriamo il nostro primo dato in blockchain](./C_interagire_con_la_blockchain/11_inseriamo_il_nostro_primo_dato_in_blockchain.md)
12. [Tecniche di Progressive Data Management](./C_interagire_con_la_blockchain/12_tecniche_di_progressive_data_management.md)
13. [Importanza delle firme blockchain](./C_interagire_con_la_blockchain/13_importanza_delle_firme_blockchain.md)
14. [Panoramica sugli account multisignature](./C_interagire_con_la_blockchain/14_panoramica_account_multisignature.md)

### D - La tokenizzazione

15. [Panoramica sul mondo dei token](./D_planum_layer_di_tokenizzazione/15_panoramica_sul_mondo_dei_token.md)
16. [Approfondimento sulle sidechain](./D_planum_layer_di_tokenizzazione/16_approfondimento_sulle_sidechain.md)
17. [Tipologie di sidechain e token](./D_planum_layer_di_tokenizzazione/17_tipologie_di_sidechain_e_token.md)
18. [Come creare una nuova sidechain](./D_planum_layer_di_tokenizzazione/18_come_creare_una_nuova_sidechain.md)
19. [Come interagire con la sidechain](./D_planum_layer_di_tokenizzazione/19_come_interagire_con_la_sidechain.md)
20. [Tools e software di supporto](./D_planum_layer_di_tokenizzazione/20_tools_e_software_di_supporto.md)

### E - Smart Contracts

21. [Panoramica generale](./E_smart_contracts/21_panoramica_generale.md)
22. [Configurazione ambiente di sviluppo](./E_smart_contracts/22_configurazione_ambiente_di_sviluppo.md)
23. [Scrittura e pubblicazione dello smart contract](./E_smart_contracts/23_scrittura_e_pubblicazione_dello_smart_contract.md)
24. [Interazione attraverso Core](./E_smart_contracts/24_interazione_attraverso_core.md)
25. [Interazione attraverso IdaNode](./E_smart_contracts/25_interazione_attraverso_idanode.md)
26. [Mantenere online uno smart contract](./E_smart_contracts/26_mantenere_online_uno_smart_contract.md)

### F - Creiamo una dApp

27. [Strutturazione progetto frontend](./F_creiamo_una_dapp/27_strutturazione_progetto_frontend.md)
28. [Creazione semplice Smart Contract](./F_creiamo_una_dapp/28_creazione_semplice_smart_contract.md)
29. [Impostazione dinamiche di login](./F_creiamo_una_dapp/29_impostazione_dinamiche_di_login.md)
30. [Interazione con lo Smart Contract](./F_creiamo_una_dapp/30_interazione_con_lo_smart_contract.md)
31. [Pubblicazione della dApp](./F_creiamo_una_dapp/31_pubblicazione_della_dapp.md)

### G - Conclusioni

32. [Identità digitale decentralizzata](./G_conclusioni/32_identita_digitale_decentralizzata.md)
33. [dApp sviluppate da Scrypta Foundation](./G_conclusioni/33_dapp_sviluppate_da_scrypta_foundation.md)
34. [Contribuire al progetto Scrypta](./G_conclusioni/34_contribuire_al_progetto_scrypta.md)
34. [Ecosistema Scrypta](./G_conclusioni/35_contribuire_al_progetto_scrypta.md)
