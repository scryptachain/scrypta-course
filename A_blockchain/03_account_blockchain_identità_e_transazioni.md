# Account blockchain

## Indirizzi

Le transazioni all'interno della blockchain fanno riferimento a specifici indirizzi. Questi indirizzi rappresentano una specifica entità che può operare in blockchain per ricevere o inviare fondi. Gli indirizzi vengono generati per mezzo della crittografia a curva ellittica, che è stata scelta da Satoshi Nakamoto quando fu creato Bitcoin per via della sua economia in termini di spazio (soprattutto se paragonata ad altre forme di crittografia come l'RSA).

Tutti gli indirizzi avranno quindi una forma simile a quella proposta sebbene non possano esisterne due uguali se opportunamente creati:

```
{
  "address": "LZW3U8usYUje6G7fv6aoaJjjmYneAu6hhF",
  "private_key": "Spfyx49FyDM5Rj5UzQn5NN7RqpE2ttm2tRyCEiZnUfFfWNtPBzMK",
  "pub_key": "037a3bb65256a2fe8fd360391107a463698232282b27e6f4c59bf8c920316642d4",
}
```

## Transazioni

Come abbiamo già detto le transazioni non sono altro che l'espressione della volontà di un indirizzo di voler muovere degli input di sua proprietà verso uno o più output. Le transazioni vengono identificate per mezzo di una `txid` che rappresenta quella particolare transazione all'interno del network. Anche qui non possono esserci due `txid` uguali per via della procedura di `hashing` utilizzata per ottenerla. 

Una transazione tipo può essere vista [qui](https://bb.scryptachain.org/tx/f550d6f4d00c82a4e54a802985e941153c1965d98168138644428fd75f794fc9) e ne riportiamo qui la sua struttura: 

```
{
  "hex": "010000000122ab893862d3e74c5c827a766d052029b322843da0a5ddae2f16d55a6c72f40a010000004847304402202dfcb468400aac79d7fecaa5ecc98daa78e1a09d4a3f1cec11ec97df67c595c4022064ccf29e718ac5ec5152829220c6653b45e7a203538803153a6fac52d7856e5e01ffffffff03000000000000000000a87566803500000023210283856511bf236a6b46406a673d566581f6b34c4b6466a4cf6931fb9df2121f29ac80c5f71c000000001976a914ce8b18e8d892acd0eb59913ef69d0351f87a45b188ac00000000",
  "txid": "f550d6f4d00c82a4e54a802985e941153c1965d98168138644428fd75f794fc9",
  "version": 1,
  "locktime": 0,
  "vin": [
    {
      "txid": "0af4726c5ad5162faedda5a03d8422b32920056d767a825c4ce7d3623889ab22",
      "vout": 1,
      "scriptSig": {
        "asm": "304402202dfcb468400aac79d7fecaa5ecc98daa78e1a09d4a3f1cec11ec97df67c595c4022064ccf29e718ac5ec5152829220c6653b45e7a203538803153a6fac52d7856e5e01",
        "hex": "47304402202dfcb468400aac79d7fecaa5ecc98daa78e1a09d4a3f1cec11ec97df67c595c4022064ccf29e718ac5ec5152829220c6653b45e7a203538803153a6fac52d7856e5e01"
      },
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "value": 0,
      "n": 0,
      "scriptPubKey": {
        "asm": "",
        "hex": "",
        "type": "nonstandard"
      }
    },
    {
      "value": 2297.87465128,
      "n": 1,
      "scriptPubKey": {
        "asm": "0283856511bf236a6b46406a673d566581f6b34c4b6466a4cf6931fb9df2121f29 OP_CHECKSIG",
        "hex": "210283856511bf236a6b46406a673d566581f6b34c4b6466a4cf6931fb9df2121f29ac",
        "reqSigs": 1,
        "type": "pubkey",
        "addresses": [
          "LWn5chmF2efvZwB6o6xoruFi7PoZpfb2MM"
        ]
      }
    },
    {
      "value": 4.86,
      "n": 2,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 ce8b18e8d892acd0eb59913ef69d0351f87a45b1 OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a914ce8b18e8d892acd0eb59913ef69d0351f87a45b188ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "Le446NzyrB5yoqA3J2Ue4eoj4CFAWvN3Hs"
        ]
      }
    }
  ],
  "blockhash": "5014f309e8269478abcec30bc00d0cf1b3361a7f3eae36eafa5003ee1841014d",
  "confirmations": 1,
  "time": 1611746582,
  "blocktime": 1611746582
}
```

Come possiamo vedere abbiamo sempre le seguenti proprietà:

- **hex**: ovvero la rappresentazione esadecimale della transazione stessa, detta anche `rawtransaction`.
- **txid**: l'id della transazione
- **version**: la versione della transazione, nel caso di Scrypta sarà sempre `1`
- **locktime**: un particolare parametro che indica se gli output sono bloccati per un determinato periodo di tempo
- **vin**: gli `utxo` in input della transazione
- **vout**: gli output della transazione, ovvero come la totalità dei fondi di input devono essere ripartiti tra gli output. Per ogni output potremo vedere sia il `value` cioè la quantità assegnata che `addresses` ovvero gli indirizzi a cui vengono assegnati i fondi
- **blockhash**: l'hash del blocco in cui viene confermata la transazione
- **confirmations**: il numero di conferme, ovvero il numero di blocchi emessi dopo l'inserimento in blockchain
- **time**: l'epoch time in cui è stata inviata la transazione
- **blocktime**: l'epoch time del blocco in cui è stata inserita

Chiaramente parte di questi parametri vengono aggiunti successivamente all'invio della transazione stessa, nello specifico le informazioni relative al blocco e alle conferme.

## Dati generici (uso di OP_RETURN)

Fino a questo momento sembra chiaro come le transazioni sono composte e come effettivamente gli indirizzi siano coinvolti all'interno della transazione stessa. Ora, da un punto di vista dello sviluppo vero e proprio, dobbiamo spiegare come inserire dei dati all'interno di queste transazioni e quindi come utilizzare quel particolare op-code chiamato `OP_RETURN`.

Analizziamo ora la transazione con txid [8bd0ebf67eaa0b4bc69622d97fa6837e9d8670e1d4adfd9b04457cc5b87b4595](https://bb.scryptachain.org/tx/8bd0ebf67eaa0b4bc69622d97fa6837e9d8670e1d4adfd9b04457cc5b87b4595), nello specifico la parte di `vin` e di `vout`:

```
 "vin": [
    {
      "txid": "1b0dc1aaeff45c60b27c793d4e4b01a642a825df7e77a1a108afc489f6f517b6",
      "vout": 0,
      "scriptSig": {
        "asm": "3044022037cbb74b4593b3fea9a6875e528280cf62737b21f00573e05f74a0693ffba652022040b0871f5d50820915df59a6f441fbb2cdfac3dc1015929614b1f561336363f201 0317d34806eefc23105b7fd30a61b8e97c2fe4c35530b762340b2ccbc537880186",
        "hex": "473044022037cbb74b4593b3fea9a6875e528280cf62737b21f00573e05f74a0693ffba652022040b0871f5d50820915df59a6f441fbb2cdfac3dc1015929614b1f561336363f201210317d34806eefc23105b7fd30a61b8e97c2fe4c35530b762340b2ccbc537880186"
      },
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "value": 0.049,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 b19f59a77c4f99a8c70854e8fd792730b6d0a6de OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a914b19f59a77c4f99a8c70854e8fd792730b6d0a6de88ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "LbR8m1kkLSiiTDaEU8sHeeeh1jGbGho8uo"
        ]
      }
    },
    {
      "value": 0,
      "n": 1,
      "scriptPubKey": {
        "asm": "OP_RETURN 2a212a35633631393331372e353166392e346265652e393163622e383131616536333235333165212a21212a21212a212a3d3e4c6f72656d20697073756d20646f6c6f722073697420616d65742c20636f6e73656374657475722061646970697363696e6720656c69742e20416c697175616d206174206c696265726f20696e206a7573746f2072757472756d2068656e64726572697420612071756973206d61676e612e2a212a",
        "hex": "6a4ca82a212a35633631393331372e353166392e346265652e393163622e383131616536333235333165212a21212a21212a212a3d3e4c6f72656d20697073756d20646f6c6f722073697420616d65742c20636f6e73656374657475722061646970697363696e6720656c69742e20416c697175616d206174206c696265726f20696e206a7573746f2072757472756d2068656e64726572697420612071756973206d61676e612e2a212a",
        "type": "nulldata"
      }
    }
  ]
```

Come possiamo leggere vediamo in input il seguente `utxo`:

```
"txid": "1b0dc1aaeff45c60b27c793d4e4b01a642a825df7e77a1a108afc489f6f517b6",
"vout": 0
```

e in output un array con due `utxo` diversi:

- Il primo vout fa riferimento all'indirizzo `LbR8m1kkLSiiTDaEU8sHeeeh1jGbGho8uo` che, facendo una ricerca a ritroso capiamo essere lo stesso [indirizzo](https://bb.scryptachain.org/tx/1b0dc1aaeff45c60b27c793d4e4b01a642a825df7e77a1a108afc489f6f517b6)

- Il secondo vout invece è composto da `OP_RETURN 2a212a3563...`. Questo particolare output contiene quindi dei dati, inseriti sottoforma di esadecimale, all'interno della transazione. Se andiamo a decodificarae i dati dall'esadecimale all'ascii otterremo questo:

```
*!*5c619317.51f9.4bee.91cb.811ae632531e!*!!*!!*!*=>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam at libero in justo rutrum hendrerit a quis magna.*!*
```

Questi sono quindi dei dati non convenzionali per la blockchain (ovvero che non fanno riferimento a transazioni) ma che possono tornare molto utili dal punto di vista dello sviluppatore!

## Progressive Data Management

In questo piccolo esercizio di lettura blockchain abbiamo scoperto uno dei principali aspetti di Scrypta. L'inserimento e la formattazione di questi dati ha permesso la creazione di quello che chiamiamo *Progressive Data Management* ovvero la tecnica di gestione dei dati non convenzionali all'interno degli IdaNode.

Approfondiremo questo aspetto più avanti, la cosa principale da capire è che grazie all'inserimento di informazioni strutturate all'interno di `OP_RETURN` possiamo effettivamente ricreare una sorta di _database decentralizzato_ (con operazioni di scrittura, lettura, update ed invalidazione) che fa capo ad uno specifico `indirizzo` e che possiamo utilizzare per creare le nostre applicazioni decentralizzate, dopo tutto i dati sono la base di qualsiasi applicazione (decentralizzata o no).
