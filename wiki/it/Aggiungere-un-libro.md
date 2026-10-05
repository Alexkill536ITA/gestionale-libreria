**Italiano** · [English](../en/Adding-a-book.md)

# Aggiungere e modificare un libro

Il pulsante **Aggiungi libro** sta in alto a destra nel catalogo. Lo stesso
modulo si riapre con la matita su una riga, per modificare.

![Il modulo vuoto](immagini/modulo-vuoto.png)

**Il titolo è l'unico campo obbligatorio.** Tutto il resto può restare vuoto.

Un libro che **non hai ancora** si mette in
[Da acquistare](Da-acquistare.md), e da lì entra in catalogo già compilato il
giorno che arriva. Ma il modulo è **questo**: «Aggiungi a mano», là dentro, apre
lo stesso dialogo in un contesto che spegne i campi di un libro che tieni in mano
— posizione, stato di lettura, data di acquisto, prezzo — e con loro la
scansione, *Elimina*, *Duplica* e *Salva e aggiungi un altro*. Tutto il resto di
questa pagina vale anche là.

## Come è diviso

Il modulo ha due colonne, e la divisione non è estetica:

- **L'esemplare** — la copia che hai in mano. Dove sta sullo scaffale, se l'hai
  letta, quanto l'hai pagata, la sua copertina.
- **L'opera** — il libro come lo conosce il mondo. Titolo, autori, editore,
  anno, serie.

Sopra le due colonne sta l'**ISBN** con i due pulsanti che fanno il lavoro al
posto tuo: **Scansiona** (accende la webcam) e **Cerca i metadati**.

## I dieci campi sempre visibili

| Campo | Note |
|---|---|
| ISBN | 10 o 13 cifre; è la chiave con cui si cercano i metadati |
| Posizione | testo libero: `SAL-1`, `Comodino`, `Prestato a Marco` |
| Stato di lettura | Da leggere · In lettura · Letto |
| Titolo | **obbligatorio** |
| Autori | uno o più, ognuno con un ruolo: Autore, Disegnatore, Traduttore, Curatore |
| Editore | |
| Anno | di questa edizione |
| Genere | uno solo |
| Serie | il nome, più il numero del volume |
| Volumi totali | quanti volumi ha la serie in tutto |

Per aggiungere un secondo autore c'è **+ Aggiungi autore**; la `×` a destra
toglie la riga. Con due autori o più, accanto al ruolo compaiono due frecce —
«Sposta più in alto» e «Sposta più in basso» — che cambiano l'ordine: il primo
della fila è quello che il catalogo nomina per primo. Sul primo la freccia in su
è spenta, e sull'ultimo quella in giù.

## Altri dettagli

Dieci campi in più stanno sotto **Altri dettagli**, chiuso all'inizio. Si apre
da sé quando una ricerca dei metadati ha riempito qualcosa là sotto — e
l'etichetta dice quanti campi sono stati compilati (`· 4 compilati`), così sai
che vale la pena guardare.

![Altri dettagli](immagini/modulo-altri-dettagli.png)

Sottotitolo, anno della prima edizione, pagine, collana, lingua, prezzo pagato
con la valuta, quando l'hai comprato, i tag, le note e la descrizione.

![Tag, note e descrizione](immagini/modulo-tag-note.png)

Due caselle meritano una riga:

- **Prezzo pagato** — vuoto vuol dire «non lo so», `0` vuol dire «gratis»: sono
  due cose diverse e restano distinte. La valuta si sceglie accanto, libro per
  libro; quale sia quella predefinita si decide nelle [Impostazioni](Impostazioni.md).
- **Acquistato** — va bene anche solo l'anno.

Diverse caselle **non ti lasciano digitare quello che verrebbe rifiutato**, così
non resta niente da scoprire al salvataggio: nel **Prezzo pagato** entrano solo
cifre e un separatore, con due decimali al massimo; in **Acquistato** solo quello
che può stare in una data; in **Anno**, **Prima edizione** e **Pagine** solo
cifre. Un carattere rifiutato **non entra e non cancella quello che c'era** — la
casella resta com'era. Lo stesso vale per il **Telefono** di una persona nei
[prestiti](I-prestiti.md), che tiene anche `+`, spazi, trattini e parentesi: sono
le forme in cui un numero si scrive.

L'**ISBN** è l'eccezione, ed è voluta: là si incolla da qualunque parte, con i
trattini e gli spazi che si porta dietro, e il codice viene ripulito da sé.
Restringere quella casella butterebbe via un codice buono sepolto in un incolla.

## I suggerimenti mentre scrivi

Sette campi ti propongono quello che hai già usato: posizione, genere, editore,
collana, lingua, serie e tag. Basta la prima lettera.

![I suggerimenti](immagini/autocomplete.png)

Non è solo comodità. Se scrivi `Manga` in un libro e `manga` in un altro, ti
ritrovi **due generi** che si dividono i conteggi nei filtri. Accettando il
suggerimento resti sulla grafia che hai già scelto.

## Entrare in una serie riempie qualche casella

Scrivi nel campo **Serie** il nome di una serie che hai già, e il modulo si
riempie da sé di quello che quella serie ha imparato dagli altri volumi: **tag,
genere, editore e collana**. I tag si aggiungono ai tuoi, i tre campi singoli
entrano **solo dove erano vuoti** — quello che hai scritto tu resta com'è. Se
qualcosa è finito sotto **Altri dettagli**, il pannello si apre da sé.

Anche i **volumi totali** arrivano da lì, se la serie ne ha uno e tu non ne hai
già scritto uno tuo.

Come una serie impara quei valori, e come si correggono per tutti i volumi in un
colpo, sta in [Le serie](Le-serie.md).

## Salvare

Tre pulsanti in fondo:

- **Salva** — salva e chiude;
- **Salva e aggiungi un altro** — salva e ripulisce il modulo restando aperto,
  con la webcam ancora accesa se stavi scansionando. È il modo di catalogare una
  pila di libri uno dietro l'altro;
- **Annulla** — chiude senza salvare.

Se hai scritto qualcosa, `Esc` e **Annulla** non chiudono subito: chiedono
conferma.

![La conferma di uscita](immagini/modulo-conferma-uscita.png)

**Uscire senza salvare butta anche le copertine appena scelte.** Un'immagine
presa da un file, da un indirizzo o dalle fonti non resta sul disco se il libro
non viene salvato. Correggere la copertina di un libro già salvato, invece, butta
la vecchia quando premi **Salva** — se nessun altro libro la usa. I dettagli
stanno in [Le copertine](Le-copertine.md).

## Un codice che non è un ISBN

I codici dei libri cominciano per `978` o `979`. Se ne scrivi uno di tredici
cifre che non è di quella famiglia — o un `978` con l'ultima cifra che non torna
— **il salvataggio non si blocca: ti fa una domanda.** In fondo al modulo compare
il codice per intero, la riga che dice che nessuna fonte lo conoscerà, e due
strade:

![La conferma di un codice non standard](immagini/modulo-conferma-isbn.png)

- **Correggi il codice** — riporta il fuoco sulla casella dell'ISBN;
- **Salva lo stesso** — lo scrive nel catalogo così com'è. I metadati di quel
  libro andranno riempiti a mano: quel codice non lo cerca nessuno.

Confermato una volta, non te lo richiede a ogni modifica di quel libro. Ma basta
che tu **tocchi il campo ISBN** perché torni a chiedere, e va bene così: un
codice storto scritto dopo una conferma non deve passare in silenzio.

Sotto le tredici cifre invece è un rifiuto, non una domanda — `97888` non è un
codice da salvare lo stesso, è un codice sbagliato.

## Modificare un libro che c'è già

La matita nel catalogo riapre lo stesso modulo con i campi pieni. Tre
differenze:

![Il modulo in modifica](immagini/confronto-modifica.png)

- il pulsante della ricerca si chiama **Aggiorna dai metadati**, e quello che
  trova non scrive sopra quello che hai: compare come pastiglie accanto ai tuoi
  valori, e decidi campo per campo;
- **quello che svuoti viene cancellato davvero.** Non resta il valore di prima:
  la casella vuota vince;
- **l'unica eccezione sono i volumi totali della serie.** Svuotare quella casella
  non azzera il totale, perché quel numero appartiene alla serie e non a questa
  copia: azzerarlo salvando *un* volume lo toglierebbe a tutti gli altri. Per
  togliere davvero un totale si passa da [Le serie](Le-serie.md).

**Elimina** sta in basso a sinistra, lontano da Salva. Accanto sta **Duplica**,
che serve quando la stessa edizione ti è entrata in casa due volte: come funziona
sta [più sotto](#duplicare-un-volume).

## Passare da un libro all'altro senza chiudere

In modifica la testata porta due frecce e dice a che punto sei: `3 di 11`.

![Le frecce per scorrere i libri](immagini/modulo-scorrimento.png)

Servono quando stai sistemando una serie intera: apri il primo volume, correggi,
freccia, correggi il secondo. Funzionano anche con `Alt`+`←` e `Alt`+`→`.

Tre cose che vale la pena sapere:

- **il conto è quello del catalogo come lo stai guardando** — con la ricerca e i
  filtri che hai attivi, e nell'ordine che hai scelto. Se hai filtrato per una
  posizione, scorri solo quei libri;
- **la pagina non ti ferma.** Arrivato all'ultimo libro della pagina, la freccia
  apre il primo della successiva e la tabella sotto volta pagina con te;
- **se hai scritto qualcosa e non l'hai salvato, la freccia chiede prima** — la
  stessa domanda di `Esc`. «Continua a scrivere» ti lascia dove sei.

Sul primo libro la freccia indietro è spenta, e sull'ultimo quella avanti.

## Duplicare un volume

Due copie dello stesso libro non sono un errore: sono **due esemplari**, e nel
catalogo stanno come due righe. Una comprata nuova e una usata, una in salotto e
una prestata, due volte lo stesso volume di una serie. In modifica, accanto a
**Elimina**, c'è **Duplica**.

**Fa una copia uno a uno del libro che hai aperto, e non la salva.** Il modulo
resta aperto e cambia mestiere: da modifica di quel libro diventa la creazione di
un altro che gli somiglia, e la testata lo dice — *Duplica il volume*, «è una
copia non ancora salvata».

![Il modulo in modo duplica](immagini/modulo-duplica.png)

Nella copia c'è tutto, **ISBN e numero del volume compresi**: è la stessa
edizione, e il secondo «15» di una serie porta lo stesso numero del primo. Tu
correggi quello che cambia — la posizione, il prezzo, lo stato di lettura — e
premi **Salva**.

Fino a quel momento **non è stato scritto niente**. `Esc` e **Annulla** chiedono
cosa farne come per qualunque libro nuovo, e «Butta le modifiche» lascia il
catalogo com'era.

Con la copia in mano tre cose spariscono, e non è una dimenticanza:

- **Elimina**, perché parlava del libro di prima;
- **le frecce** che scorrono il catalogo, con il loro `3 di 11`: quel conto nomina
  la riga da cui sei partito, e la copia non è ancora nel catalogo;
- **Salva e aggiungi un altro**, che azzererebbe il modulo invece di rifare
  un'altra copia. In fondo restano **Annulla** e **Salva**.

La **copertina diventa un file suo**, copiato subito e non al salvataggio. Le due
righe non condividono l'immagine, quindi eliminando uno dei due libri l'altro non
resta senza; e cambiare la copertina della copia non tocca quella del libro di
partenza. Se abbandoni la copia senza salvarla, quel file se ne va con lei e la
copertina del libro di partenza resta dov'è.

Sotto l'ISBN comparirà *«ne hai già uno con questo ISBN»*: **è giusto così, e non
ti ferma.** Il libro con quel codice esiste davvero, ed è quello da cui sei
partito — quello che hai in mano è il secondo esemplare.
