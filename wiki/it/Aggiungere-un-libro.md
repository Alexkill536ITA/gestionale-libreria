**Italiano** · [English](../en/Adding-a-book.md)

# Aggiungere e modificare un libro

Il pulsante **Aggiungi libro** sta in alto a destra nel catalogo. Lo stesso
modulo si riapre con la matita su una riga, per modificare.

![Il modulo vuoto](immagini/modulo-vuoto.png)

**Il titolo è l'unico campo obbligatorio.** Tutto il resto può restare vuoto.

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
| Autori | uno o più, ognuno con un ruolo (Autore, Disegnatore, Traduttore…) |
| Editore | |
| Anno | di questa edizione |
| Genere | uno solo |
| Serie | il nome, più il numero del volume |
| Volumi totali | quanti volumi ha la serie in tutto |

Per aggiungere un secondo autore c'è **+ Aggiungi autore**; la `×` a destra
toglie la riga.

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

## I suggerimenti mentre scrivi

Sette campi ti propongono quello che hai già usato: posizione, genere, editore,
collana, lingua, serie e tag. Basta la prima lettera.

![I suggerimenti](immagini/autocomplete.png)

Non è solo comodità. Se scrivi `Manga` in un libro e `manga` in un altro, ti
ritrovi **due generi** che si dividono i conteggi nei filtri. Accettando il
suggerimento resti sulla grafia che hai già scelto.

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

**Elimina** sta in basso a sinistra, lontano da Salva.
