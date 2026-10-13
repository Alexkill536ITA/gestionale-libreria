**Italiano** · [English](../en/The-catalogue-on-a-server.md)

# Il catalogo su un server

Di partenza il catalogo è un file su questo computer. Se hai un database che
risponde in rete — un NAS, un server di casa, un servizio in affitto — il
catalogo può stare **lì**, e le pagine leggono e scrivono di là.

Tutto si fa in **Impostazioni → Database**, nel gruppo **Da solo**:
**Su un tuo database**.

## A cosa serve, e cosa non è

Nel gruppo **Da solo** la sezione ha due pallini, **Su questo computer** e **Su
un tuo database** — il terzo, **Col servizio della biblioteca**, è raccontato in
[Dove stanno i dati](Dove-stanno-i-dati.md#col-servizio-della-biblioteca) — e
quello acceso dice **quale catalogo stai guardando**. Scegliere «Su un tuo
database» apre il
server subito, **senza riavviare**: le pagine si rileggono da sole e da lì in
poi tutto quello che fai — un libro, un prestito, una serie — si scrive sul
server.

**Il catalogo di questo computer resta intatto.** Non viene svuotato, non viene
spostato e non si aggiorna: sono **due cataloghi**, non due copie che si
tengono allineate. Riaccendendo «Su questo computer» ritrovi il tuo file
esattamente com'era il giorno che l'hai lasciato.

E va detto con onestà cosa **non** è: **non è un programma multiutente.** Non
ci sono account né permessi, e chiunque abbia il collegamento può fare tutto.
Due computer possono aprire lo stesso catalogo, ma se due persone modificano
**lo stesso libro** nello stesso momento vince chi salva per ultimo, e le
modifiche dell'altro spariscono senza avviso. Per una famiglia che si divide
gli scaffali va benissimo; per un ufficio dove dieci persone catalogano
insieme, no.

**Per più persone c'è il servizio della biblioteca**, la terza strada: un
programma che tiene il catalogo su un computer solo, dove ognuno entra col suo
nome e fa solo quello che i suoi permessi gli consentono, e dove un libro aperto
da uno si vede «in modifica» dagli altri invece di essere sovrascritto. Come si
installa lo dice [Installare il servizio](Installare-il-servizio.md), come ci si
lavora [Lavorare in biblioteca](Lavorare-in-biblioteca.md).

## Quali database fanno da catalogo

Si sceglie prima la famiglia — **SQL** o **MongoDB** — e poi il **Motore**.

Ricevono un catalogo in quattro:

- **PostgreSQL**
- **MySQL**
- **SQL Server**
- **MongoDB**, a una condizione: dev'essere avviato come **replica set**. Va
  bene anche un nodo soltanto, ma un server semplice viene rifiutato con:

  > Questo MongoDB è un server solo, e il catalogo ha bisogno di un replica
  > set: senza, un ripristino interrotto lascerebbe il catalogo vuoto. Va bene
  > anche un nodo soltanto, purché avviato come replica set.

Gli altri due della tendina, **MariaDB** e **SQLite (file di rete)**, si
configurano e si provano, ma **non ricevono un catalogo**. Se accendi «Su un
tuo database» con uno di loro, la finestra si ferma sulla schermata del catalogo che
non si apre — con il file di rete il titolo è «Il catalogo nel file di rete non
si apre» — e con la frase:

> «mariadb» non sa ancora ricevere un catalogo: per adesso lo fanno PostgreSQL,
> MySQL, SQL Server e MongoDB.

Da lì si torna indietro con **Usa il catalogo di questo computer**.

## Compilare il collegamento

I campi sono quelli di qualunque programma che parla a un database:

- **Host** — il nome o l'indirizzo del server;
- **Porta** — **si riempie da sé** con quella del motore: 3306 per MySQL, 5432
  per PostgreSQL, 1433 per SQL Server, 27017 per MongoDB. Cambiando motore si
  aggiorna; una porta che hai scritto tu invece resta;
- **Nome del database** — quello dove vivrà il catalogo;
- **Utente** e **Password**;
- **Collegamento cifrato (TLS)** — se il server lo offre, utente e password non
  viaggiano in chiaro;
- **Database di autenticazione**, che compare **solo con MongoDB**: è il
  database dove l'utente è definito, che non è per forza quello dei dati. Un
  utente di amministrazione vive in `admin`, uno creato apposta per
  questa applicazione nel database che usa. **Vuoto vale `admin`.**

**La password si scrive e resta a pallini.** Non compare nella schermata del
server che non risponde, né nello
[storico delle azioni](Lo-storico-delle-azioni.md), dove un cambio di password
dice soltanto `presente` o `assente`.

**Tutto si salva da sé**, come il resto della finestra, anche a metà: una bozza
lasciata a mezzo non si perde.

**Se il server è già acceso**, cambiare il collegamento salva la configurazione
nuova mentre scrivi, ma il catalogo si riapre **quando chiudi le impostazioni**:
così un indirizzo scritto a metà non fa sparire la finestra. Se il collegamento
nuovo non risponde, alla chiusura compare la schermata del server che non
risponde, con le sue due uscite.

## Dove stanno le copertine

Sotto **Copertine** tre voci dicono dove stanno le immagini del catalogo che
sta sul server:

- **Dentro il database** — le immagini viaggiano col database: un solo posto
  da salvare, e un database che cresce in fretta;
- **Cartella** — il database resta leggero e le immagini stanno in una
  cartella condivisa, **che va raggiungibile da ogni computer** che apre quel
  catalogo. Qui una cartella di rete va bene, al contrario del catalogo di
  questo computer: si sceglie con **Sfoglia** o si scrive, ma dev'essere un
  percorso completo;
- **Archivio S3** — le immagini stanno su un servizio compatibile con S3 (Amazon
  S3, MinIO, Backblaze B2 e simili), che ogni computer raggiunge dalla rete:
  nessun disco da condividere.

La scelta di partenza è **Cartella**.

L'archivio S3 vuole cinque campi: **Indirizzo del servizio**, **Contenitore**,
**Regione**, **Chiave** e **Segreto**. La regione è l'unico che si può lasciare
vuoto, e allora vale `us-east-1`; il segreto resta a pallini come la password.

### Il posto lo decide il catalogo

Con il catalogo del server aperto, il posto delle copertine **è del catalogo**:
vale per ogni computer che lo apre, e la sezione lo dice sotto il titolo. Una
riga dice **quante copertine ci sono, quanto pesano, dove stanno** e che da
questo computer **si vedono**.

Chiave e segreto di un archivio S3 **restano su ogni computer**, nel riquadro
**Di questo computer**, e non entrano nel catalogo: ogni computer mette i suoi.

### Cambiare posto è un gesto solo

Scegliere un'altra voce, o scrivere un'altra cartella, **non salva niente**: è
una bozza. Sotto compare un riquadro che dice quante copertine vanno nel posto
nuovo, da dove partono e dove arrivano, e porta **Sposta le copertine qui**.

Il pulsante **copia** le immagini con una barra che conta, e **solo a copia
finita** il catalogo dice il posto nuovo: fino ad allora ogni computer continua
a usare quello di prima, quindi nessuno vede mai un posto vuoto. Le copie
rimaste nel posto di prima **non le cancella il programma**: quando sei sicuro
che nel posto nuovo ci sono tutte, le togli tu. **Annulla** riporta la bozza al
posto del catalogo.

Gli altri computer se ne accorgono da soli, entro mezzo minuto. Se il posto
nuovo è un archivio, chi non ne ha la chiave vede i libri col dorso e un avviso
con due caselle per metterla: **Usa questa chiave** la prova prima di tenerla, e
se l'archivio la rifiuta lo dice.

**Una lettera d'unità è di un computer solo.** `Z:` su un altro computer può
essere un altro disco, o mancare: per una cartella condivisa la sezione consiglia
il percorso di rete, come `\\nas\libreria\copertine`. Se la cartella del
catalogo da questo computer non si apre, un avviso lo dice, con **Riprova**.

Se prima di questa versione questo computer teneva le copertine in un posto suo,
diverso da quello del catalogo, e qualcuna è rimasta lì, un avviso le conta e
offre di spostarle dove le tiene il catalogo, così le vedono tutti.

Con il catalogo **su questo computer** la stessa scelta dice dove andranno le
copertine quando porti il catalogo sul server, e si salva da sola come il resto
della sezione.

## Provare il collegamento

**Prova il collegamento** si accende quando host, porta e nome del database ci
sono, e apre una connessione vera: utente e password vengono verificati fino in
fondo, e se va bene la riga verde dice il motore, la versione che il server
dichiara e quanti millisecondi ci ha messo a rispondere.

La prova guarda anche le copertine: una **Cartella** viene provata
**scrivendoci** un file e cancellandolo, un **Archivio S3** scrivendo,
rileggendo e cancellando un oggetto di prova. Con MongoDB verifica anche il
replica set.

Quando non va, dice **quale** cosa non va:

- «Il server non risponde: controlla l'indirizzo, la porta e che sia acceso.»
- «Il server ha rifiutato utente e password.»
- «Sul server non c'è nessun database che si chiami «libreria».»
- «L'utente non può entrare nel database «libreria»: o non esiste, o non gli è
  stato concesso.»
- «Questo server chiede di cifrare la password per poterla verificare: accendi
  «Collegamento cifrato (TLS)» e riprova.» — è il caso tipico di MySQL 8 appena
  installato;
- «Il collegamento cifrato non è riuscito: il server potrebbe non offrire TLS.»
- «Il server ci ha messo troppo a rispondere.»
- «Non riesco a scrivere nella cartella delle copertine «…».»
- «L'archivio delle copertine non risponde: controlla l'indirizzo, il
  contenitore e che il servizio sia acceso.»
- e, se manca un campo dell'archivio, la frase che dice quale: l'indirizzo, il
  contenitore, la chiave o il segreto.

La prova dice se il server risponde, non se il catalogo che c'è dentro è
buono: quello si scopre quando il catalogo si apre, come racconta più sotto
«Un database vuoto si prepara da sé».

## Portare di là il catalogo che hai

Il caso più comune è avere già duecento libri su questo computer e volerli sul
server. Lo fa **Porta qui il catalogo di questo computer**, in fondo alla
sezione.

Il pulsante chiede conferma, e la conferma conta i libri **di questo
computer**, cioè quelli che stanno per partire:

> 212 libri di questo computer stanno per essere copiati su
> nas.local:5432/libreria.

**Porta il catalogo** fa il travaso: prima le copertine, poi i libri, le
serie, i prestiti e il resto. Alla fine una banda verde dice quanti libri e
quante copertine sono arrivati.

Il travaso **porta i dati, ma non cambia il catalogo che stai guardando**:
quello lo decide il pallino. Finito il giro, per lavorare sul server scegli
«Su un tuo database». E il catalogo di questo computer resta com'è: sul server ne
arriva una copia.

Il pulsante resta spento, o il gesto si rifiuta, in questi casi:

- **il collegamento non è completo**, oppure il salvataggio automatico non ha
  ancora scritto l'ultima modifica: il travaso usa la configurazione salvata, e
  premere prima parlerebbe a un server diverso da quello che hai a schermo.
  Aspetta un istante e si riaccende;
- **il motore non riceve un catalogo** (MariaDB, SQLite): sotto il pulsante
  una riga lo dice;
- **sul server c'è già un catalogo**:

  > Su quel server c'è già un catalogo, con 40 libri dentro: portarci sopra
  > questo ne mescolerebbe due.

- **il catalogo di questo computer è vuoto**:

  > Il catalogo di questo computer è vuoto: non c'è niente da portare sul
  > server.

In tutti questi casi non viene scritto niente, né di qua né di là.

## Un database vuoto si prepara da sé

Non serve preparare tabelle o collezioni a mano. **Un database vuoto, la prima
volta che il programma lo apre, diventa un catalogo**: succede quando accendi
«Su un tuo database» o quando ci porti il catalogo di questo computer.

Due casi invece vengono rifiutati, perché nessuno dei due si ripara da solo:

- un catalogo **rimasto a metà**, interrotto mentre nasceva:

  > Il catalogo di quel server è rimasto a metà, alla versione 3: è stato
  > interrotto mentre nasceva, e riprenderlo da capo sopra quello che c'è già
  > lo rovinerebbe.

- un catalogo scritto da **un'altra versione** del programma:

  > Quel catalogo è alla versione 5 dello schema, e questa versione del
  > programma ne scrive un'altra.

Nel secondo caso la strada è di solito aggiornare il programma su questo
computer, così che tutti i computer che aprono quel server abbiano la stessa
versione.

## Quando il server non risponde

Server spento, rete che non arriva, password cambiata: il programma **non
ripiega sul catalogo di questo computer** e non ti mostra una finestra di libri
che non sono quelli che hai chiesto. Si ferma su una schermata:

> **Il catalogo sul server non si apre**

Sotto c'è l'indirizzo del server nella forma `utente@host:porta/database` —
**mai la password** — e il motivo. Da lì si esce con due pulsanti:

- **Riprova** — riacceso il server o tornata la rete, riapre il catalogo
  **senza riavviare**;
- **Usa il catalogo di questo computer** — riaccende «Su questo computer» e
  riapre il tuo file.

E l'ultima riga è quella che conta: **non è stato cancellato niente.** Il
catalogo del server è dov'era, e quello di questo computer non è stato toccato.

**Se il server cade mentre lavori, la schermata arriva da sola.** Il programma
se ne accorge appena una pagina chiede qualcosa al server, e anche se stai
guardando una pagina ferma: ogni **30 secondi**, e solo mentre la finestra è
visibile, controlla che il server risponda ancora.

## Le copertine che non si caricano

Se il posto delle copertine non risponde — la cartella condivisa è spenta,
l'archivio S3 non è raggiungibile — i titoli restano e le immagini diventano
**dorsi disegnati**, come per un libro che una copertina non l'ha mai avuta
(vedi [Le copertine](Le-copertine.md)).

Quando il posto torna raggiungibile, **le immagini non ricompaiono da sole**:
tornano cambiando pagina o riaprendo la vista.

Le **copie ridotte** delle copertine — quelle piccole del catalogo e delle
righe, e quelle intermedie dei riquadri più grandi — si fanno la prima volta
che servono e **si tengono su questo computer**. Così, dopo la prima apertura,
sfogliare è veloce anche con le immagini su un server lontano. Il rovescio è
che una copia ridotta può continuare a vedersi qui anche se l'originale di là
non c'è più.

## Backup, esportazione, import e ripristino

Funzionano tutti e quattro **anche con il catalogo sul server**, e riguardano
il catalogo che stai guardando. Come si usano è in
[Backup e ripristino](Backup-e-ripristino.md); con il server acceso cambiano
tre cose:

- **il backup nasce in una cartella di questo computer**, quella della sezione
  Backup, anche se il catalogo sta di là. Lo stesso vale per il file CSV
  dell'esportazione. Un backup preso dal server si può ripristinare anche su
  questo computer, e viceversa;
- **l'import da un foglio** aggiunge i libri al catalogo del server;
- **il ripristino non riavvia il programma.** Prima fa un backup di sicurezza
  del catalogo del server, poi lo **sostituisce in un colpo solo** con quello
  dell'archivio, e alla fine dice:

  > Il catalogo sul server è stato sostituito con quello dell'archivio.

  Ricorda che quel catalogo **lo usano tutti i computer collegati**: un
  ripristino riporta indietro anche loro.

## Lo storico delle azioni

Con il server acceso, la pagina dello [storico](Lo-storico-delle-azioni.md)
mostra **lo storico del server**: quello che fai su libri, serie, editori e
prestiti si scrive di là, accanto ai dati che descrive.

Gli eventi che nascono dalle impostazioni — `Impostazioni`,
`Database configurato`, `Catalogo spostato` e `Catalogo portato sul server` —
restano invece **nello storico di questo computer**, perché parlano di questo
computer e non del catalogo. Mentre guardi il server non li vedi: ricompaiono
quando torni a «Su questo computer».

Lo storico si accende e si spegne dalle Preferenze, una volta per tutti e due
i cataloghi, e spegnerlo **li svuota tutti e due**: quello del server, cioè gli
eventi che la conferma ha contato, e quello di questo computer, dove stanno gli
eventi delle impostazioni. Se il server non risponde, lo storico **non si
spegne**: la casella resta accesa e compare l'errore, invece di spegnersi
lasciando di là quello che la conferma aveva promesso di cancellare. Lo storico del server si accorcia a un anno ogni
volta che il catalogo si apre, e un ripristino lascia di là il suo evento
«Ripristino».

## Dove sta la configurazione

Il collegamento sta in `impostazioni.json`, nella cartella dei dati di questo
computer; **la password del database e il segreto dell'archivio S3 no**: stanno
nel portachiavi del sistema, sotto la voce «Gestionale Libreria - impostazioni»,
e restano nel file solo se il portachiavi manca o li rifiuta (vedi
[Dove stanno i dati](Dove-stanno-i-dati.md)). **Niente di tutto questo entra nei
backup**: su un altro computer il collegamento va riscritto a mano, e lo stesso
se reinstalli.

Un'ultima cosa che confonde: nell'elenco delle sezioni delle
[Impostazioni](Impostazioni.md), la riga sotto **Database** conta i libri **di
questo computer**, non quelli del server. Anche quando lavori di là, quel
numero parla del file che hai qui.
