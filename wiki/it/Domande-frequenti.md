**Italiano** · [English](../en/FAQ.md)

# Domande frequenti

## Windows dice che il programma non è sicuro

SmartScreen avvisa perché **il programma non ha una firma digitale**. Non è un
segnale che il file sia stato manomesso. **Ulteriori informazioni** → **Esegui
comunque**. Le ragioni sono in [Installazione](Installazione.md).

## Gira su un Mac?

In ogni versione c'è un `.dmg`, uno solo per i Mac Intel e per quelli con Apple
Silicon — ma **nessuno l'ha ancora aperto su un Mac**, quindi non è una promessa:
è un tentativo. Il programma è nato per Windows, ed è su Windows che è stato
provato in una finestra vera, funzione per funzione.

Se lo provi, la cosa più utile è raccontare com'è andata — soprattutto lo scanner
della webcam e le copertine, i due pezzi che dipendono più di tutti dal sistema.
Il file da scaricare e come si passa l'avviso di macOS stanno in
[Installazione](Installazione.md).

## Ho disinstallato: ho perso il catalogo?

No. **La disinstallazione non cancella i dati.** Reinstalla e ritrovi tutto.
Il catalogo sta in
`%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\` e resta lì.

## Non trovo il programma in `Programmi`

Non è lì: l'installazione è per il solo utente corrente, quindi il programma sta
in `%LOCALAPPDATA%\Gestionale Libreria\`.

## Ho cercato un ISBN e non ha trovato niente

Vuol dire che **nessuna delle quattro fonti conosce quell'edizione**. Capita con
la saggistica italiana di piccoli editori e con certe edizioni di nicchia.

Cosa provare, nell'ordine:

1. **cerca per titolo** — svuota l'ISBN, scrivi titolo e autore, e premi lo
   stesso pulsante;
2. se è **manga**, cerca per titolo comunque: AniList compare solo lì, e su
   quello è la fonte migliore;
3. **controlla le cifre** dell'ISBN: se ne manca una l'applicazione lo rifiuta
   («ISBN non valido: …»), mentre se sono tredici ma il codice non è di quelli
   dei libri ti chiede se salvarlo lo stesso — e in quel caso nessuna fonte lo
   conoscerà mai, per quanto tu riprovi;
4. compila a mano. Non è una sconfitta: le fonti non sanno tutto.

## Una fonte risponde con un errore HTTP

`Google ha risposto con un errore (HTTP 503)` e simili vengono **dal catalogo
remoto**, non dall'applicazione. Sono quasi sempre passeggeri: riprova fra
qualche minuto. Le altre fonti intanto hanno risposto lo stesso.

Se **Google Books** sbaglia sempre, controlla la chiave in Impostazioni →
Metadati con il pulsante **Verifica**.

## Dove trovo questa guida, dal programma?

Il **punto interrogativo** in alto a destra, accanto all'ingranaggio: apre queste
pagine nel browser, nella lingua che stai usando. Cambiando lingua dalle
[Impostazioni](Impostazioni.md) cambia anche la pagina che si apre.

## Sono sparite le scritte accanto alle icone in alto

La finestra è troppo stretta perché ci stiano. **Catalogo**, **Serie** ed
**Editori** restano al loro posto come icone, e fermandoci sopra il puntatore si
legge il nome: allargando la finestra le scritte tornano da sole.

La ricerca sta al centro della finestra, e per restarci ha bisogno che a sinistra
e a destra ci sia lo stesso spazio: quando non ce n'è abbastanza, a cedere sono
le scritte — prima finivano *sopra* la casella di ricerca.

## Il mirino della webcam è nero

Windows ha scelto una fotocamera virtuale (OBS, FaceRig, NVIDIA Broadcast) che
non trasmette niente. Usa la tendina **Fotocamera** sotto il mirino e scegli
quella vera. Dettagli in
[Scansionare il codice a barre](Scansionare-il-codice-a-barre.md).

## All'avvio mi ha detto che c'è una versione nuova: si è aggiornato da solo?

No. **L'applicazione non scarica e non installa niente.** L'avviso legge l'elenco
delle versioni pubblicate e ti dice cosa cambia; «Aggiorna ora» apre solo la
pagina nel browser, dove scarichi il file quando vuoi. Poi si installa sopra, e i
dati restano dove sono.

Se non ti interessa quella versione, **Salta questa versione**: non te lo ricorda
più finché non ne esce un'altra. Se non vuoi più nessun controllo all'avvio, la
spunta si toglie da Impostazioni → Aggiornamenti. Tutto il giro è in
[Aggiornamenti](Aggiornamenti.md).

## Ho premuto «Cerca aggiornamenti» e dice che non c'è nessuna versione pubblicata

Non è un guasto: vuol dire che **nessuna versione è ancora stata pubblicata**, e
quella che hai è l'unica che esiste. Succede finché non viene messa online la
prima.

## Ho lo stesso libro due volte

Se le due righe sono davvero due copie tue, va bene così: sono due esemplari,
magari uno prestato. Se invece è un doppione per sbaglio, elimina una riga col
cestino.

Quando scansioni un ISBN che hai già, l'applicazione te lo dice — *«ne hai già
uno con questo ISBN»* — ma non ti ferma, proprio perché due copie sono
legittime.

## Ho due generi uguali: `Manga` e `manga`

Non dovrebbe più capitare: l'applicazione riusa la grafia che hai scelto la
prima volta, anche a maiuscole e accenti diversi. Se hai due voci nate prima,
riapri i libri della grafia sbagliata e scegli quella giusta **dai suggerimenti**
invece di riscriverla: quando l'ultimo libro l'abbandona, la voce sparisce dai
filtri.

## Nella colonna Autore vedo un trattino

Il campo è vuoto, non c'è un errore. Vale per tutte le colonne: `—` significa
«non compilato».

## La ricerca non trova un libro che c'è

Tre cose da controllare:

- **hai un filtro attivo?** Il conteggio in alto e i chip sotto il titolo lo
  dicono. Prova **Azzera tutto**;
- **stai cercando in un campo indicizzato?** La barra guarda titolo,
  sottotitolo, autori, tag, editore, collana e note — **non** la descrizione né
  il nome della serie;
- **stai cercando l'inizio di una parola?** La ricerca lavora per prefisso:
  `camil` trova `Camilleri`, ma un pezzo preso in mezzo alla parola no.

Se hai sbagliato a scrivere, l'applicazione se ne accorge da sola e mostra i
libri che somigliano.

## Come sposto tutto su un altro computer

Con un backup. Copia lo `.zip` più recente, installa l'applicazione sul computer
nuovo e usa **Ripristina da un backup…**. Tornano libri e copertine; tema,
lingua e chiave API si rimettono a mano.
Il giro completo è in [Backup e ripristino](Backup-e-ripristino.md).

## Posso usarlo su due computer insieme?

No, e non conviene provarci. Non c'è sincronia: diventerebbero due cataloghi
distinti, e ripristinare l'uno sull'altro cancellerebbe il lavoro del secondo.

Peggio ancora è mettere la cartella dei dati dentro OneDrive o Dropbox: la
sincronia sui file del database può **corromperlo**. Sincronizza i backup, non
il catalogo.

## Ho cancellato un libro per sbaglio

Non si annulla. L'unica strada è [ripristinare un backup](Backup-e-ripristino.md),
che però riporta indietro **tutto** il catalogo allo stato di quel giorno — e
quindi perdi anche quello che hai fatto dopo.

## L'applicazione parte in inglese

La lingua sta nelle Impostazioni e vale dall'avvio dopo. Se è cambiata da sola,
qualcuno l'ha cambiata lì: Impostazioni → Preferenze → Lingua.

## Ho cambiato il totale di una serie ma nel modulo del libro non cambia

I due posti non fanno la stessa cosa. Il totale **appartiene alla serie**: si
corregge in `/serie`, e da lì si può anche togliere. La casella nel modulo del
libro serve a scriverlo la prima volta — svuotarla non lo azzera, apposta.
Spiegazione in [Le serie](Le-serie.md).
