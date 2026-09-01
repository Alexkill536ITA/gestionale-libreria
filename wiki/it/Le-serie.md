**Italiano** · [English](../en/Series.md)

# Le serie

La voce **Serie** nella barra risponde a una domanda sola: **quali volumi mi
mancano?**

![La vista delle serie](immagini/serie.png)

Una serie compare qui appena scrivi il suo nome nel modulo di un libro. Non c'è
niente da preparare prima.

## Come si legge una riga

![Una riga di serie](immagini/serie-riga.png)

Da sinistra:

- **il nome** della serie;
- **quanti ne hai su quanti** — `2 / 20`. Il totale sta in una casella
  modificabile: correggilo lì e basta, si salva da solo;
- **quali mancano**, con i buchi accorpati: `mancano 2, 4–20` invece di
  diciotto numeri in fila;
- a destra, la pastiglia con il conto: `mancano 18 volumi`;
- sotto, **la fila dei dorsi**: copertina vera per i volumi che hai, riquadro
  tratteggiato col numero per quelli che mancano.

L'ordine dell'elenco non è alfabetico: **in cima i totali da correggere** — le
serie dove hai più volumi di quanti il totale dichiari, che è il segno di un
totale sbagliato — poi quelle a cui manca meno, e in fondo le complete.

## Aggiungere una serie

**Aggiungi serie**, in alto a destra.

![Aggiungere una serie](immagini/serie-aggiungi.png)

Il nome basta. Il totale si può lasciare vuoto, e conviene farlo quando la serie
è ancora in corso: senza totale, l'applicazione non ti dirà mai che manca il
volume dopo l'ultimo che hai.

I volumi si catalogano dopo, dal modulo del libro, scrivendo quel nome nel campo
Serie.

## Modificare ed eliminare

Passa il puntatore su una riga: a destra compaiono la matita e il cestino.

![Le azioni di una serie](immagini/serie-riga-azioni.png)

La matita cambia nome e totale. Il cestino chiede conferma:

![La conferma di eliminazione](immagini/serie-elimina.png)

Attenzione alla spunta, che è **attiva di default**:

- **spuntata** — spariscono anche i volumi catalogati, con le loro copertine;
- **tolta** — i volumi restano nel catalogo e perdono soltanto serie e numero.

Non si annulla. Una serie senza volumi non mostra la spunta, perché non c'è
niente da portarsi dietro.

## Il totale dei volumi: due strade

Lo stesso numero si tocca in due posti, e non fanno la stessa cosa:

| Dove | Cosa succede svuotando la casella |
|---|---|
| **Qui, in `/serie`** | il totale sparisce davvero |
| Nel modulo di un libro | **non** succede niente: il totale resta |

La differenza è voluta. Quel numero appartiene alla serie, non alla singola
copia: se svuotare la casella nel modulo lo azzerasse, salvare *un* volume
cancellerebbe il totale per tutti gli altri. La casella nel modulo serve perché
è lì che il totale arriva da AniList senza che tu debba digitarlo.

## Una serie vuota non sparisce

Una serie aggiunta a mano resta nell'elenco anche senza volumi, e anche dopo un
riavvio. Se non la vuoi più, si toglie con il suo cestino.
