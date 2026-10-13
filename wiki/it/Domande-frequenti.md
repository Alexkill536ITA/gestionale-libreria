**Italiano** · [English](../en/FAQ.md)

# Domande frequenti

## Windows dice che il programma non è sicuro

SmartScreen avvisa perché **il programma non ha una firma digitale**. Non è un
segnale che il file sia stato manomesso. **Ulteriori informazioni** → **Esegui
comunque**. Le ragioni sono in [Installazione](Installazione.md).

## Gira su un Mac?

Sì. In ogni versione c'è un `.dmg`, uno solo per i Mac Intel e per quelli con
Apple Silicon, ed è stato aperto e provato. Il programma è nato per Windows, ma
su un Mac funziona.

Al primo avvio macOS avvisa lo stesso, perché non c'è un certificato pagato ad
Apple: come si passa quell'avviso sta in [Installazione](Installazione.md),
insieme al file da scaricare. Se qualcosa non torna, raccontalo — soprattutto lo
scanner della webcam e le copertine, i due pezzi che dipendono più di tutti dal
sistema.

## Ho disinstallato: ho perso il catalogo?

No. **La disinstallazione non cancella i dati.** Reinstalla e ritrovi tutto.
Il catalogo sta in
`%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\` e resta lì — se non
l'hai spostato in un'altra cartella, nel qual caso è dove l'hai messo, e se non
sta su un server, dove la disinstallazione non arriva affatto. Dove sta di
preciso te lo dice Impostazioni → Database; il resto è in [Dove stanno i
dati](Dove-stanno-i-dati.md).

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

`Google ha risposto con un errore (HTTP 503)` e simili vengono **dal servizio
della fonte**, non dall'applicazione. Sono quasi sempre passeggeri: riprova fra
qualche minuto. Le altre fonti intanto hanno risposto lo stesso.

Se **Google Books** sbaglia sempre, controlla la chiave in Impostazioni →
Metadati con il pulsante **Verifica**.

## Dove trovo questa guida, dal programma?

Il **punto interrogativo** in alto a destra, accanto all'ingranaggio: apre queste
pagine nel browser, nella lingua che stai usando. Cambiando lingua dalle
[Impostazioni](Impostazioni.md) cambia anche la pagina che si apre.

## Sono sparite le scritte accanto alle icone in alto

La finestra è troppo stretta perché ci stiano. **Catalogo**, **Serie**,
**Editori** e **Prestiti** restano al loro posto come icone, e fermandoci sopra
il puntatore si legge il nome: allargando la finestra le scritte tornano da sole.

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

## Non riesco a eliminare un libro: dice che ce l'ha qualcuno

È in prestito, e finché è fuori non si elimina — né col cestino del catalogo né
con la spunta che porta via i volumi di una serie. Il messaggio nomina chi ce
l'ha: fattelo restituire da **Prestiti → Registra una restituzione**, e poi
eliminalo.

Non è una prudenza esagerata: il prestito aperto è la sola cosa che dice che quel
volume non è sullo scaffale, e portarlo via lo farebbe risultare disponibile
mentre è a casa di qualcuno.

## Ho letto il codice a barre di un libro che torna, e dice che è in casa

Vuol dire che per il registro quel libro non è mai uscito, e ci sono due
possibilità: o non l'avevi mai registrato come prestito, o **il codice letto è di
un altro libro**. Su un volume ce ne sono stampati due o tre — il prezzo, il
codice interno del negozio — e lo scanner legge quello che gli capita davanti.

Riprova inquadrando il codice sotto l'ISBN, oppure passa dall'altra via: **Chi te
lo riporta**, che mostra solo i libri che quella persona ha davvero fuori. Il
giro completo è in [I prestiti](I-prestiti.md).

## A chi ho prestato questo libro?

Non serve aprire la pagina dei prestiti: nel catalogo, la cella **Letto** del
libro porta un segno accanto allo stato di lettura, e fermandoci sopra il
puntatore si legge il nome, la data e da quanto tempo è via.

Per vederli tutti insieme, il filtro **Prestito → fuori casa**, oppure la voce
**Prestiti** nella barra.

## Come segno un libro che devo ancora comprare?

Non nel catalogo: c'è **Da acquistare**, la voce a destra della ricerca. Scrivi
l'ISBN o il titolo, scegli l'edizione, e il volume resta lì con il suo prezzo
finché non lo compri — poi **Aggiungi a catalogo** lo porta dentro già
compilato. La lista si riempie **un volume per volta**: non dice quale numero ti
manca di una serie, perché quel dato le fonti non lo danno. Tutto in
[Da acquistare](Da-acquistare.md).

## Ho due generi uguali: `Manga` e `manga`

Non dovrebbe più capitare: l'applicazione riusa la grafia che hai scelto la
prima volta, anche a maiuscole e accenti diversi. E se due voci sono nate prima,
non serve passare dai libri: **tag, autori, generi, collane, posizioni e
lingue** si correggono da [I dizionari del
catalogo](I-dizionari-del-catalogo.md), dove `Manga` e `manga` diventano uno
solo con **Unisci in un altro**.

Gli unici valori che restano fuori da quella pagina sono l'**editore**, che ha
la sua — [Gli editori](Gli-editori.md), con gli alias — e i valori delle
**serie**, che si correggono da [Le serie](Le-serie.md).

## Un autore compare due volte, uno in giapponese e uno in caratteri latini

Sono due nomi della stessa persona, e nessun confronto di lettere può unirli: le
fonti giapponesi scrivono `アネコユサギ`, le altre `Yusagi Aneko`. Si uniscono da
**I dizionari del catalogo** — dall'ingranaggio in alto a destra — con **Unisci
in un altro**: scegli il nome che resta, e i libri dell'altro passano a lui. Lo
stesso vale per due tag che dicono la stessa cosa.

Da lì si **rinomina** anche una grafia sbagliata e si **toglie** un valore che
non usa più nessuno. Il giro completo è in
[I dizionari del catalogo](I-dizionari-del-catalogo.md).

## Ho spento lo storico delle azioni: dov'è finito quello che aveva registrato

Cancellato — e la domanda che compare quando togli la spunta lo dice, con quanti
eventi porta via. «Spento» qui vuol dire che di quello che hai fatto non resta
niente, non che si smette di scrivere sopra un elenco che rimane. Riaccendendolo
riparte da zero, e il primo evento registrato è l'accensione stessa. Tutto in
[Lo storico delle azioni](Lo-storico-delle-azioni.md).

## Ordino il catalogo per anno, lo riapro e torna com'era

Il clic sull'intestazione vale per questa sessione e non si ricorda. L'ordine da
cui il catalogo **parte** si sceglie in Impostazioni → Preferenze →
**Ordinamento del catalogo**, e senza una scelta è l'aggiunta più recente. È
voluto: un ordine che si salvasse da sé cambierebbe le carte in tavola a ogni
clic distratto.

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

Con un backup. Fanne uno con **Crea backup adesso** — nessuno nasce da sé —
copia lo `.zip`, installa l'applicazione sul computer nuovo e usa **Ripristina
da un backup…**. Tornano libri e copertine; tema, lingua, chiave API e il
collegamento al server, se ne usi uno, si rimettono a mano: stanno nelle
impostazioni, che nel backup non entrano.
Il giro completo è in [Backup e ripristino](Backup-e-ripristino.md).

Se il catalogo sta su un server, non c'è niente da spostare: sul computer nuovo
rifai il collegamento da Impostazioni → Database, e i libri sono quelli di
sempre. Come si fa è in [Il catalogo su un server](Il-catalogo-su-un-server.md).

## Posso usarlo su due computer insieme?

Sì, **mettendo il catalogo su un server**: PostgreSQL, MySQL, SQL Server o
MongoDB. Le copertine vanno in un posto che tutti i computer raggiungono —
**dentro il database**, **in un archivio S3** o in una **cartella condivisa** —
e da lì ogni computer vede gli stessi libri. Il giro è in [Il catalogo su un
server](Il-catalogo-su-un-server.md).

Così, però, non è un programma per più persone: su un tuo database non ci sono
account, e se due modificano lo stesso libro insieme vince chi salva per ultimo,
senza che l'altro lo sappia. **Per più persone c'è il servizio della
biblioteca**: ognuno entra col suo nome, coi suoi permessi, e un libro aperto da
uno si vede «in modifica» dagli altri. Lo raccontano [Installare il
servizio](Installare-il-servizio.md) e [Lavorare in
biblioteca](Lavorare-in-biblioteca.md).

Due copie del catalogo di questo computer, invece, restano due cataloghi
distinti: non si parlano, e ripristinare l'uno sull'altro cancellerebbe il
lavoro del secondo. E la cartella del catalogo dentro OneDrive o Dropbox si può
tenere, ma aperta **su un computer per volta**: due scritture insieme sul file
del database lo **danneggiano**. Il perché sta in [Dove stanno i
dati](Dove-stanno-i-dati.md).

## Il servizio dice che è a un'altra versione

«Il servizio è alla versione …, questo programma a un'altra: aggiorna quello dei
due che è indietro.» L'app e il servizio si parlano solo se la versione è
**identica**, fino all'ultima cifra. Si aggiorna quello che è rimasto indietro —
di solito l'app, come dice [Aggiornamenti](Aggiornamenti.md) — e conviene
aggiornarli sempre insieme. Come si aggiorna il servizio sta in [Installare il
servizio](Installare-il-servizio.md#aggiornare).

## Ho dimenticato la password del servizio

La password del servizio la reimposta un amministratore, o chi gestisce gli
utenti, da **Utenti e gruppi**: lo racconta [Utenti, gruppi e
permessi](Utenti-gruppi-e-permessi.md). Se a perderla è l'amministratore, sulla
macchina del servizio si fa nascere un codice di configurazione nuovo, come dice
[Installare il servizio](Installare-il-servizio.md#il-codice-perso-o-la-password-dellamministratore).
Una password del dominio, invece, si cambia nel dominio.

## Una versione precedente non salva un libro «Lasciato»

Da questa versione lo stato di lettura ha un quarto valore, **Lasciato**: un
libro cominciato e messo da parte. Una versione precedente del programma apre
ancora un catalogo che ne contiene, ma **rifiuta di salvare** quei libri — dice
«Stato di lettura sconosciuto» — e nell'import da un foglio lascia fuori le
righe che lo portano. Succede soprattutto con un catalogo su un tuo database
aperto da computer con versioni diverse. Il rimedio è aggiornare il programma su tutti i computer. Col servizio
il problema non si pone: un'app di un'altra versione non si collega affatto.

## Come porto i miei libri sul server?

Da Impostazioni → Database, con il collegamento compilato, **Porta qui il
catalogo di questo computer** e poi **Porta il catalogo**. Sul server ne arriva
una **copia**, copertine comprese; il catalogo di questo computer resta com'era.
Per lavorare di là, poi, scegli **Su un tuo database**.

Si fa solo verso un catalogo del server ancora vuoto: se di là ci sono già dei
libri, il gesto si rifiuta invece di mescolarne due. Tutto in [Il catalogo su
un server](Il-catalogo-su-un-server.md).

## Il server non risponde, cosa faccio?

Se il server smette di rispondere — spento, la rete che non ci arriva, le
credenziali cambiate — al posto delle pagine compare «Il catalogo sul server non
si apre». **Non si è perso niente**, né di là né di qua. Quando il server torna,
**Riprova**; se devi lavorare subito, **Usa il catalogo di questo computer**,
sapendo che è un altro catalogo (vedi sotto). Il resto è in [Il catalogo su un
server](Il-catalogo-su-un-server.md).

## MongoDB non va bene: dice che è un server solo

Il catalogo su MongoDB vuole un **replica set**, perché senza non esistono le
operazioni che si annullano tutte insieme — e un ripristino interrotto lascerebbe
il catalogo vuoto. Va bene anche un nodo soltanto, purché avviato come replica
set. Come si fa sta in [Il catalogo su un
server](Il-catalogo-su-un-server.md).

## Posso tornare al catalogo di questo computer?

Sì: Impostazioni → Database, pallino **Su questo computer**. Ma sono **due
cataloghi, non due copie**: quello che hai fatto sul server resta sul server, e
qui ritrovi il catalogo com'era quando l'hai lasciato.

Per portarti qui il lavoro fatto di là: con il server ancora scelto fai un
backup con **Crea backup adesso**, poi passa a **Su questo computer** e
[ripristina](Backup-e-ripristino.md) quell'archivio. Il catalogo di questo
computer viene sostituito per intero.

## Posso fare il backup del catalogo sul server?

Sì, con lo stesso pulsante: **Crea backup adesso** archivia il catalogo che
stai usando, e con il server scelto è quello di là, con le copertine da
qualunque posto stiano. Lo zip finisce comunque **su questo computer**, nella
cartella dei backup. Dettagli in [Backup e ripristino](Backup-e-ripristino.md).

## Ho ripristinato sul server e non si è riavviato

È giusto così, e la conferma lo dice. Sul server non c'è
nessun file da sostituire al riavvio: il catalogo viene svuotato e ricaricato in
un colpo solo, le pagine si rileggono subito, e l'esito è «Il catalogo sul
server è stato sostituito con quello dell'archivio.» Il riavvio serve solo al
catalogo di questo computer.

## Ho cambiato dove stanno le copertine: si spostano da sole?

No, e la scelta non si salva nemmeno da sola: con il catalogo su un server è una
bozza, e il posto cambia solo con **Sposta le copertine qui**, che le copia e a
copia finita lo scrive nel catalogo, per tutti i computer. Quelle di prima
restano dove sono.

## Perché una copertina appare come un dorso?

Un dorso disegnato è quello che l'applicazione mostra al posto di un'immagine
che non ha: o quel libro una copertina non ce l'ha, o **il posto delle copertine
non ha risposto** — una cartella condivisa non raggiungibile, un archivio S3
spento. Nel secondo caso le copertine tornano da sole quando il posto risponde
di nuovo, **cambiando pagina o riaprendo la vista**: finché la vista resta
quella, il dorso resta. Vedi [Le copertine](Le-copertine.md).

## Ho cancellato un libro per sbaglio

Non si annulla. L'unica strada è [ripristinare un backup](Backup-e-ripristino.md)
— se ne hai fatto uno, perché il programma non ne fa da sé — e comunque riporta
indietro **tutto** il catalogo allo stato di quel giorno, storico delle azioni
compreso, quindi perdi anche quello che hai fatto dopo. Col catalogo su un
server il ripristino riscrive il catalogo **di tutti** i computer collegati.

## L'applicazione parte in inglese

La lingua sta nelle Impostazioni e **cambia subito**, senza riavviare. Se è
cambiata da sola, qualcuno l'ha cambiata lì: Impostazioni → Preferenze →
Lingua.

## Ho cambiato il totale di una serie ma nel modulo del libro non cambia

I due posti non fanno la stessa cosa. Il totale **appartiene alla serie**: si
corregge in `/serie`, e da lì si può anche togliere. La casella nel modulo del
libro serve a scriverlo la prima volta — svuotarla non lo azzera, apposta.
Spiegazione in [Le serie](Le-serie.md).
