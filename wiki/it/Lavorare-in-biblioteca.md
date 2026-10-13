**Italiano** · [English](../en/Working-in-a-library.md)

# Lavorare in biblioteca

Questa pagina è per chi lavora sul catalogo di una biblioteca attraverso il suo
**servizio**, con un nome e dei permessi dati da qualcun altro. Il resto della
guida vale anche per te — aggiungere un libro, cercare, prestare si fanno allo
stesso modo —, e qui c'è solo quello che cambia quando il catalogo è di tutti.

Come si mette in piedi il servizio e come si danno i permessi lo raccontano
[Installare il servizio](Installare-il-servizio.md) e
[Utenti, gruppi e permessi](Utenti-gruppi-e-permessi.md).

## Entrare

La prima volta servono l'**indirizzo del servizio** e il modo di entrare, che ti
dà chi lo gestisce. L'indirizzo si scrive nella [guida al primo
avvio](Installazione.md#il-primo-avvio), scegliendo **In una biblioteca** e poi
**Mi collego al servizio della biblioteca**, oppure più tardi in
**Impostazioni → Database**, **Col servizio della biblioteca**. Al primo
collegamento l'app mostra l'impronta del servizio: confrontala con quella che ti
dà chi lo gestisce, e se è uguale premi **Mi fido**.

Poi si apre da solo il dialogo **Entra nel servizio**. Secondo come è fatto il
servizio, chiede nome e password, l'account del dominio, apre il browser di un
fornitore di accesso, o propone **Entra come …** col tuo nome di Windows: ogni
caso è raccontato in [I modi di entrare](I-modi-di-entrare.md).

Entrato una volta, **riaprendo il programma non serve rientrare** finché la
sessione è viva.

## Il menu col tuo nome

Nella barra in alto compare il tuo nome. Cliccandolo si apre un menu, che dice
se sei **Amministratore** o **Utente** e a quale servizio sei collegato, e
tiene:

- **I miei prestiti…** — vedi più sotto;
- **Utenti e gruppi…** — solo per chi gestisce gli utenti;
- **Cambia la password…** — solo se entri con la password del servizio;
- **Esci**, che chiude la sessione e riapre il dialogo per entrare.

## Cosa vedi, secondo i permessi

Quello che puoi fare lo decidono i tuoi gruppi. Un **Lettore**, per esempio,
vede il catalogo e nient'altro; il **Bancone** presta e riprende i libri; il
**Redattore** cataloga. Chi entra dal dominio senza stare in nessun gruppo della
biblioteca lo sa subito, da un avviso: «Entri come Lettore».

**Le voci che non ti servono spariscono dalla barra.** Senza il permesso di
vedere i prestiti non c'è **Prestiti**, senza quello della lista degli acquisti
non c'è **Da acquistare**, senza quello dello storico non c'è **Storico delle
azioni** nel menu dell'ingranaggio.

**I gesti che non puoi fare si vedono spenti, e dicono perché.** Sotto il
pulsante una frase nomina il permesso che manca:

> Il tuo utente non ha il permesso «Fare un backup del catalogo»: chiedilo a un
> amministratore del servizio.

Succede col backup, l'esportazione, l'import da un foglio, il ripristino,
l'interruttore dello storico e la barra della lista degli acquisti.

**Un libro che non puoi modificare si apre in sola lettura.** Il modulo si
intitola «Il libro, in sola lettura», sotto il titolo la stessa frase nomina il
permesso, e in fondo resta solo **Chiudi**. Senza il permesso di aggiungere
libri non c'è **Aggiungi libro**, e un catalogo vuoto dice soltanto «Quando
qualcuno aggiungerà un libro, comparirà qui.»

**I contatti delle persone possono mancare.** Senza il permesso «Vedere email e
telefono delle persone», nei prestiti le persone compaiono col loro nome e
basta: il servizio quei contatti non li manda proprio.

Se un amministratore ti toglie un permesso mentre lavori, il gesto dopo si
rifiuta con «Il tuo utente non ha il permesso di farlo: chiedilo a un
amministratore del servizio.»

## Un libro che sta modificando un altro

Quando qualcuno apre un libro per modificarlo, il servizio glielo **prenota**:
finché lo tiene aperto, gli altri lo possono guardare ma non salvare. Così due
persone non si sovrascrivono a vicenda.

Nel catalogo, in fondo alla riga di quel libro, al posto dei pulsanti compare
una pastiglia col nome di chi lo sta modificando: «In modifica da …: si apre in
sola lettura». Aprendolo, il modulo dice «Lo sta modificando …: qui lo vedi
com'è salvato adesso.»

- **Quando l'altro salva**, il tuo modulo si rilegge da solo: i campi cambiati
  portano il segno «aggiornato», e in fondo si legge «… ha salvato alle …: qui
  c'è già la versione nuova.»;
- **quando l'altro chiude**, compare «… l'ha lasciato.», con **Modifica ora**:
  il modulo resta com'è finché non lo chiedi tu;
- **se ti serve subito**, e hai il permesso «Togliere la prenotazione di un
  altro», c'è **Togli la prenotazione**. Ti chiede conferma — «Il suo modulo
  smette di salvare, e quello che non ha ancora salvato lo perde. Il libro passa
  a te.» — e il pulsante è **Togli e modifica**.

**La prenotazione si rinnova da sola** finché il modulo è aperto, e **scade
dopo due minuti** in cui il servizio non sente più quel computer: un portatile
chiuso o una rete caduta non bloccano un libro per sempre. Chi perde la
prenotazione — scaduta, o tolta da un altro — se lo sente dire nel suo modulo,
che da lì **non salva più**: quello che hai scritto resta lì finché non lo
chiudi, se vuoi copiarlo, e **Butta le modifiche** lo chiude.

La prenotazione è del computer, non della persona: lo stesso libro aperto da te
su due computer diversi, sul secondo risulta «in modifica».

## Le modifiche degli altri, in diretta

Quello che fanno gli altri ti arriva da solo: il catalogo, le serie, gli
editori, i prestiti e la lista degli acquisti **si rileggono senza che tu faccia
niente**, senza un avviso. Se il collegamento cade per un momento, al ritorno
l'app rilegge tutto.

## I miei prestiti

**I miei prestiti…**, dal menu col tuo nome, mostra i libri che hai preso dalla
biblioteca, come li ha segnati il bancone: prima quelli da restituire, poi
quelli chiusi. Lo vede chiunque sia entrato, senza un permesso a parte, e
mostra **solo i tuoi**. Un libro lo segna restituito il bancone, quando lo
riporti.

Perché funzioni, il tuo utente dev'essere collegato alla tua persona nel
registro dei prestiti. Se non lo è, la finestra dice «Non sei ancora nel
registro dei prestiti»: ti collega chi gestisce gli utenti, da **Utenti e
gruppi**.

## Le mie letture

Col servizio **ognuno ha le sue letture**. Lo stato di lettura di un libro — Da
leggere, In lettura, Letto, Lasciato — è il **tuo**: la colonna «Letto» del
catalogo, il filtro, l'ordinamento e i libri letti contati negli editori parlano
delle tue letture. **Nessuno vede quelle degli altri**, nemmeno un
amministratore, e lo stato si cambia anche da Lettore.

- Si cambia cliccando la cella **Letto** del catalogo, che apre un menu, oppure
  nel modulo del libro, dove si salva subito, senza «Salva» — anche quando il
  libro è in sola lettura;
- **Lasciato** è un libro cominciato e messo da parte;
- le date si scrivono da sole — quando lo cominci, quando lo finisci o lo
  lasci — e si correggono nella fascia **Le mie letture** del modulo, che elenca
  tutte le volte che l'hai letto;
- **Rileggi**, su un libro letto o lasciato, comincia una lettura nuova senza
  cancellare le altre;
- tornare a **Da leggere** da un libro finito chiede conferma, perché cancella
  il tuo registro di quel libro. Gli altri non perdono il loro.

Le letture non entrano nello [storico delle azioni](Lo-storico-delle-azioni.md).

## Lo storico firmato

Col servizio, ogni riga dello [storico delle azioni](Lo-storico-delle-azioni.md)
dice **chi** ha fatto il gesto, in una colonna «Chi», col nome con cui è
entrato. Lo storico si vede col permesso «Vedere lo storico», e solo se è
acceso.

## Quando il servizio non risponde

Se il servizio è spento, o la rete non ci arriva, al posto delle pagine compare
**«Il catalogo sul servizio non si apre»**, anche a lavoro iniziato. **Non si è
cancellato niente.** Quando il servizio torna, **Riprova**; **Usa il catalogo di
questo computer** apre invece il catalogo che hai qui, che è un altro catalogo.

Se è la sessione a essere finita — scaduta, o chiusa da chi gestisce il
servizio — compare **«Il servizio chiede di entrare»**, con **Entra**.

E se l'app e il servizio non sono della **stessa versione**, non si parlano:
«Il servizio è alla versione …, questo programma a un'altra: aggiorna quello
dei due che è indietro.» Di solito tocca all'app: aggiornala come dice
[Aggiornamenti](Aggiornamenti.md), o chiedi a chi gestisce il servizio.
