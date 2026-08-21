# QA Video Redactor

Oscura automaticamente i dati personali nei video: email, telefoni, IBAN, codici
fiscali, indirizzi, nomi e — su richiesta — volti e documenti.

Tutto avviene **sul tuo computer**: nessun video viene caricato da nessuna parte.

## Download

**[Scarica l'ultima versione](https://github.com/kuramalab/QA-Video-Redactor-Release/releases/latest)**

L'installatore pesa pochi MB. Al primo avvio l'applicazione riconosce il
computer e scarica i componenti adatti: circa 2,5 GB con una scheda NVIDIA
(elaborazione accelerata), circa 350 MB senza.

## Come funziona

1. **Scegli il video** — il risultato viene salvato accanto all'originale, come
   `nomefile_blur1.mp4`.
2. **Indica cosa oscurare** — categorie di dati personali e termini specifici.
3. **Regola il motore** — precisione, stile dell'offuscamento, margine.
4. **Elaborazione** — l'intelligenza artificiale legge i fotogrammi; quelli
   identici al precedente vengono saltati, così anche i computer senza scheda
   dedicata restano utilizzabili.
5. **Esito** — anteprima, registro dei dati trovati con timecode e verdetto
   della verifica.

Al termine una **verifica automatica** rilegge il video prodotto e segnala
qualunque dato ancora leggibile: è ciò che rende il file consegnabile senza
controlli manuali.

## Requisiti

| | Minimo | Consigliato |
|---|---|---|
| Sistema | Windows 10 a 64 bit (build 1809 o successiva) | Windows 11 |
| Processore | x86-64 con AVX2, 4 core | 8 core o più |
| Memoria | 8 GB | 16 GB |
| Spazio su disco | 6 GB con scheda NVIDIA · 2 GB senza | 10 GB |
| Scheda video | facoltativa: NVIDIA con 4 GB di memoria e driver 527 o successivo | NVIDIA con 6 GB o più |
| Rete | necessaria solo alla prima configurazione | — |

Lo spazio serve alle librerie di riconoscimento, che l'applicazione scarica una
sola volta: circa 5,4 GB nella versione con accelerazione CUDA, circa 1,2 GB in
quella per processore.

**Consumi misurati** durante l'elaborazione di un video 1920×1080:

- memoria: circa 1,2 GB per il motore, più l'interfaccia
- memoria video: circa 1,8 GB quando l'accelerazione è attiva

**Tempi indicativi** per 17 secondi di registrazione schermo a 1080p, con
verifica finale attiva:

| Computer | Tempo |
|---|---|
| Con scheda NVIDIA (RTX 4070 Ti) | circa 1 minuto |
| Solo processore (Intel i7 12ª generazione) | circa 6 minuti |

I fotogrammi identici al precedente non vengono rianalizzati: su una
registrazione schermo il risparmio arriva all'80%, ed è ciò che rende
l'elaborazione praticabile anche senza scheda dedicata. Su video in movimento
continuo il risparmio non c'è, e i tempi salgono di conseguenza.

## Versione

Attuale: **1.1.0** — vedi la pagina [Rilasci](https://github.com/kuramalab/QA-Video-Redactor-Release/releases)
per il registro delle modifiche.

---

Progetto e sviluppo: **Genny Sirianni** · kuramalab@gmail.com — KuramaLab
