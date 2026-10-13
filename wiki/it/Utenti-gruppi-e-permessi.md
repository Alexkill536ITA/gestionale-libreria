**Italiano** · [English](../en/Users-groups-and-permissions.md)

# Utenti, gruppi e permessi

Col catalogo sul [servizio della biblioteca](Installare-il-servizio.md) ognuno
entra col suo nome, e ogni gesto — aggiungere un libro, prestarlo, fare un
backup — chiede il suo **permesso**. I permessi si danno per **gruppi**, e chi
gestisce il servizio decide chi sta in quale gruppo.

Questa pagina è per chi gestisce gli utenti. Come si entra la racconta
[I modi di entrare](I-modi-di-entrare.md); cosa vede chi lavora, senza essere
amministratore, la racconta [Lavorare in biblioteca](Lavorare-in-biblioteca.md).

**Tutto questo vale solo col servizio.** Su questo computer e su un tuo database
non ci sono utenti né permessi: chi apre il programma può fare tutto.

## L'amministratore

Il primo utente del servizio è l'**amministratore**: nasce col codice di
configurazione, come dice [I modi di entrare](I-modi-di-entrare.md#il-primo-amministratore).
L'amministratore ha **tutti i permessi**, anche quelli che arriveranno con le
versioni future, e non dipende dai gruppi.

Gli amministratori possono essere più d'uno: nel dettaglio di un utente la
casella **Amministratore** lo fa diventare tale. Due limiti:

- **l'ultimo amministratore attivo non si disattiva e non perde la casella**:
  prima se ne fa un altro;
- **chi entra dal dominio, da un fornitore di accesso o con Kerberos non diventa
  amministratore.** Per esserlo serve un utente con la password del servizio.

## Il dialogo «Utenti e gruppi»

Il tuo nome, nella barra in alto, apre un menu; dentro c'è **Utenti e gruppi…**,
che compare a chi è amministratore o ha il permesso «Gestire gli utenti».

Il dialogo ha due lati, **Utenti** e **Gruppi**; il secondo lo vede solo un
amministratore. In fondo una riga lo ricorda: «Ogni modifica vale subito, per
tutti i computer collegati.»

Nell'elenco degli utenti, accanto ai nomi, compaiono **Amministratore**,
**Disattivato**, **tu** e **in attesa del primo accesso** — quest'ultimo per chi
è stato aggiunto dal dominio e non è ancora entrato.

### Un utente nuovo

**Nuovo utente** apre un dialogo che chiede il nome, poi la **Password** e
**Ripeti la password**: almeno otto caratteri. Il servizio non manda messaggi,
quindi nome e password li dai tu alla persona. Il pulsante è **Crea l'utente**.

Con Active Directory acceso, in testa al dialogo c'è **Come entra**:

- **Con una password** — la strada di sopra;
- **Dal dominio** — si scrive solo l'**Account di dominio**, e il pulsante è
  **Aggiungi dal dominio**. La password è quella del dominio, e qui non se ne
  sceglie nessuna. Nome a schermo e gruppi arrivano dal dominio al primo
  accesso; fino ad allora l'utente resta «in attesa del primo accesso». Vale
  anche per chi entra con Kerberos.

Chi entra da un fornitore di accesso (OIDC) non si aggiunge: nasce da solo al
primo accesso.

Un amministratore spunta anche i **gruppi** dell'utente nuovo. Senza nessun
gruppo spuntato, l'utente entra nel gruppo **Lettore** e vede solo il catalogo.

### Il dettaglio di un utente

Cliccando un utente se ne apre il dettaglio:

- **Nome a schermo** — quello che si legge nella barra e negli elenchi, con
  **Salva**. Il nome con cui si entra invece **non si cambia**, ed è quello con
  cui lo storico firma. Per chi viene dal dominio o da un fornitore, il nome a
  schermo lo dà quello, e si aggiorna a ogni accesso;
- **Reimposta la password** — solo per chi entra con la password del servizio:
  scegli la **Password nuova**, **Ripetila** e premi **Reimposta**. Le sessioni
  aperte di quella persona si chiudono, e rientra con la password nuova;
- **Disattiva** — l'utente non può più entrare, e le sue sessioni si chiudono
  subito. Gruppi e permessi restano com'erano, e tornano validi con
  **Riattiva**, che lo fa rientrare con la password di prima;
- **Sessioni** — una per ogni computer da cui è entrato, con l'ultimo uso e
  quando scade. **Chiudi la sessione** fa uscire quel computer: al gesto dopo gli
  si chiede di entrare di nuovo. **Chiudi tutte** le chiude tutte;
- **Nel registro dei prestiti** — vedi più sotto;
- **Amministratore**, **Gruppi** e **Permessi in aggiunta** — li cambia solo un
  amministratore.

**Gli utenti non si eliminano**: si disattivano. Le righe dello
[storico](Lo-storico-delle-azioni.md) che hanno firmato restano col loro nome.

### Collegare un utente a una persona dei prestiti

Gli utenti del servizio e le persone del [registro dei prestiti](I-prestiti.md)
sono due elenchi diversi. Nel dettaglio di un utente, **Nel registro dei
prestiti** ha **Collega a una persona…**: si cerca la persona per nome o
cognome — in cima quelle che portano lo stesso nome dell'utente — e si preme
**Collega**. **Scollega** toglie il legame.

Da quel momento l'utente, in **I miei prestiti**, vede i prestiti di quella
persona e solo i suoi. Una persona sta con un utente solo: se è già di un altro,
prima la si scollega da lui.

## I gruppi

Un utente ha **la somma dei permessi dei suoi gruppi**. Chi resta senza gruppi
torna nel gruppo **Lettore**, che è quello di chi non sta in nessun altro: per
questo si può rinominare ma non eliminare.

Il servizio nasce con tre gruppi:

- **Redattore** — chi cataloga: libri, serie, editori, dizionari, la lista degli
  acquisti, lo storico, il backup e l'esportazione;
- **Bancone** — chi presta: i prestiti, le restituzioni e le persone, coi loro
  contatti;
- **Lettore** — vede il catalogo, e nient'altro.

**Amministratore non è un gruppo**: è la casella di un utente, e nella matrice è
una colonna fissa che ha tutto.

Il lato **Gruppi** del dialogo è una **matrice**: una riga per permesso, una
colonna per gruppo, e una casella da accendere o spegnere in ogni incrocio. Lo
vede e lo cambia solo un amministratore.

- **Nuovo gruppo** ne crea uno senza permessi, come ultima colonna;
- il menu di un gruppo ha **Rinomina…**, **Elimina il gruppo…** — chi ci stava
  esce e tiene i permessi degli altri suoi gruppi, e chi resta senza torna
  Lettore —, **Gruppo di Active Directory…** e **Gruppo di Keycloak…** (col
  nome del fornitore), che lo legano a un gruppo del dominio o del fornitore.
  Chi entra da lì riceve i gruppi così, a ogni accesso, e nel suo dettaglio non
  si cambiano.

I tre gruppi di partenza nascono una volta sola, col servizio: uno eliminato non
torna.

## Tutti i permessi

| Permesso | Redattore | Bancone | Lettore |
|---|:-:|:-:|:-:|
| Vedere il catalogo | ✓ | ✓ | ✓ |
| Aggiungere libri | ✓ | | |
| Modificare libri | ✓ | | |
| Eliminare libri | ✓ | | |
| Importare da un foglio | ✓ | | |
| Togliere la prenotazione di un altro | | | |
| Creare e modificare serie | ✓ | | |
| Eliminare serie | ✓ | | |
| Unire editori e togliere alias | ✓ | | |
| Rinominare, unire ed eliminare voci dei dizionari | ✓ | | |
| Vedere i prestiti | ✓ | ✓ | |
| Prestare un libro | | ✓ | |
| Registrare una restituzione | | ✓ | |
| Dimenticare una persona | | ✓ | |
| Vedere email e telefono delle persone | | ✓ | |
| Vedere la lista degli acquisti | ✓ | ✓ | |
| Modificare la lista degli acquisti | ✓ | | |
| Vedere lo storico | ✓ | | |
| Accendere e spegnere lo storico | | | |
| Gestire gli utenti | | | |
| Fare un backup del catalogo | ✓ | | |
| Esportare il catalogo | ✓ | | |
| Ripristinare un archivio | | | |
| Portare un catalogo sul servizio | | | |
| Spostare le copertine | | | |

L'amministratore li ha tutti. Tre note:

- **«Vedere email e telefono delle persone»** non apre nessun gesto: chi non ce
  l'ha vede le persone del registro senza i loro contatti, e il servizio non
  glieli manda nemmeno;
- **«Spostare le copertine»** sta sotto «Arrivano più avanti»: esiste, ma
  nessun gesto lo chiede ancora;
- **«Fare un backup del catalogo»** vale anche per vedere le copie che il
  servizio tiene e per scaricarne una. Ripristino e «Portare un catalogo sul
  servizio» non stanno in nessun gruppo di partenza: di partenza li fa solo un
  amministratore. Il giro è in [Backup e ripristino](Backup-e-ripristino.md).

### Permessi in aggiunta

Nel dettaglio di un utente, **Permessi in aggiunta** dà a lui solo un permesso
che i suoi gruppi non hanno. È **solo in aggiunta**: qui non si toglie niente, e
un permesso che arriva da un gruppo compare acceso e fermo, con «dal gruppo …».
Per toglierlo si cambia la matrice, o i gruppi dell'utente.

## Chi gestisce gli utenti senza essere amministratore

Il permesso **Gestire gli utenti** si può dare anche a chi non è amministratore.
Quella persona vede il dialogo, ma col solo lato **Utenti**, e con dei limiti:

- **crea solo Lettori**: un utente nuovo, con la password o dal dominio, senza
  gruppi e senza permessi in aggiunta;
- **gruppi, permessi e la casella Amministratore non li cambia**: «Solo un
  amministratore cambia gruppi e permessi.»;
- **su un amministratore non agisce**: «Su un amministratore agisce solo un
  amministratore.»;
- **agisce solo su chi non può più di lui.** Reimpostare la password, cambiare il
  nome a schermo, disattivare, riattivare e chiudere le sessioni riescono solo
  su un utente i cui permessi stanno tutti dentro i suoi. Altrimenti il servizio
  risponde: «Questo utente può fare cose che il tuo non può: lo gestisce un
  amministratore, o chi ha almeno i suoi permessi.»

Così nessuno, gestendo gli utenti, si fa largo nei permessi di un altro.
