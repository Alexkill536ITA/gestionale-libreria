**Italiano** · [English](../en/Ways-to-sign-in.md)

# I modi di entrare

Col catalogo sul [servizio della biblioteca](Installare-il-servizio.md) ognuno
entra col suo nome, e il servizio sa chi è e cosa può fare. I modi di entrare
sono quattro: **la password del servizio**, **Active Directory**, **un fornitore
di accesso OIDC** (Keycloak, per esempio) e **Kerberos**. Quali sono accesi lo
decide chi gestisce il servizio, nel suo file `servizio.json`; di partenza c'è
solo la password.

Qualunque sia il modo, quello che si può fare dopo non cambia: lo dicono i
gruppi e i permessi, raccontati in
[Utenti, gruppi e permessi](Utenti-gruppi-e-permessi.md).

## Con la password del servizio

È il modo di partenza. Quando il catalogo sta sul servizio e questo computer non
è ancora entrato, si apre da solo il dialogo **Entra nel servizio**, con
l'indirizzo e l'impronta confermata in testa, **Nome** e **Password**, e il
pulsante **Entra**. Nome e password li dà chi gestisce il servizio.

### Il primo amministratore

Un servizio appena installato non ha nessun utente, e allora il dialogo è **Crea
il primo amministratore**: chiede il **Codice di configurazione**, poi **Nome**,
**Password** e **Ripeti la password**, e il pulsante è **Crea
l'amministratore**. La password vuole almeno otto caratteri.

Il codice lo scrive il servizio nel file `codice-di-configurazione.txt`, nella
sua cartella dati, e nel suo registro all'avvio; su Windows lo mostra anche
l'ultima pagina dell'installazione. È di dodici fra lettere e cifre, senza
quelle che si confondono (0 e O, 1, I e L), e **vale una volta sola**: creato
l'amministratore, il file sparisce.

Chi ha perso la password dell'amministratore fa nascere un codice nuovo sulla
macchina del servizio con l'opzione `--nuovo-codice` — i comandi per ogni
sistema stanno in
[Installare il servizio](Installare-il-servizio.md#il-codice-perso-o-la-password-dellamministratore).
Con quel codice si torna al dialogo: col **nome che c'era**, quell'utente torna
amministratore con la password nuova; con un nome nuovo nasce un amministratore
in più.

## Con Active Directory

Il servizio chiede al dominio se nome e password sono giusti, con un
collegamento **LDAPS** cifrato: la password del dominio non passa mai in chiaro
e il servizio non la tiene.

Il dialogo diventa **Account di dominio** e **Password del dominio**. L'account
si scrive come `nome`, o col dominio davanti: `BIBLIO\nome`.

**Non basta essere nel dominio: bisogna essere stati aggiunti.** Un amministratore
crea l'utente da **Utenti e gruppi → Nuovo utente**, sceglie **Dal dominio** e
preme **Aggiungi dal dominio**, scrivendo solo l'account: la password è quella
del dominio, e qui non se ne sceglie nessuna. Fino al primo accesso l'utente
resta «in attesa del primo accesso»; quando entra, il servizio prende dal
dominio il **nome a schermo** e i **gruppi**. Chi il dominio riconosce ma nessuno
ha aggiunto si sente rispondere come a una password sbagliata.

**I gruppi arrivano dal dominio, a ogni accesso.** Nella matrice dei gruppi, il
menu di un gruppo ha **Gruppo di Active Directory…**, che lo lega a un gruppo
del dominio; anche i gruppi annidati contano. Chi non sta in nessun gruppo
legato entra come **Lettore**, e un avviso glielo dice: «Entri come Lettore».

Se il dominio non risponde, gli amministratori hanno **Entra come amministratore
del servizio**: la loro password del servizio, che non passa dal dominio.

Una password del dominio scaduta, o che il dominio chiede di cambiare, si cambia
in Windows — Ctrl+Alt+Canc e «Cambia una password» — e poi si entra con quella
nuova.

> **Non ancora provato su una macchina vera.** Active Directory è stato provato
> solo contro un dominio Samba. Su un dominio Windows vero mancano ancora tre
> cose: il channel binding, la firma LDAP imposta dal dominio e i certificati
> distribuiti dai criteri di gruppo; e il messaggio della password scaduta
> l'hanno visto solo i test.

## Con un fornitore di accesso (OIDC)

Se la biblioteca ha già un fornitore di accesso — Keycloak, o un altro che parla
OIDC — si entra da lì. Il dialogo mostra **Entra con Keycloak** (o col nome
del fornitore che il servizio dichiara), con sotto «Si apre il browser di
questo computer.»

Premuto il pulsante, si apre la pagina del fornitore nel **browser di sistema**,
e il dialogo diventa **Continua nel browser**. Si entra lì, come si fa sempre
col fornitore; finito, l'app se ne accorge da sola e il dialogo si chiude. Se la
pagina non si vede:

- **Riapri il browser** la apre di nuovo;
- **Copia l'indirizzo** la copia, per incollarla a mano nel browser che vuoi;
- **Annulla**, o Esc, ferma tutto.

Il tentativo resta aperto **cinque minuti**: dopo bisogna ricominciare da
«Entra». **Entra con un altro nome** fa chiedere di nuovo le credenziali al
fornitore, quando il browser ricorda già qualcuno.

**Qui non serve essere aggiunti**: al primo accesso l'utente nasce da solo. I
gruppi arrivano dal fornitore a ogni accesso, e nella matrice si legano con
**Gruppo di Keycloak…** (col nome del fornitore). Chi non sta in nessun gruppo
legato entra come **Lettore**.

## Con Kerberos

Su un computer del dominio Windows sa già chi sei: con Kerberos acceso il dialogo
mostra l'**Account di Windows** con cui hai aperto la sessione, «verificato», e
il pulsante **Entra come …** col tuo nome. Non si scrive nessuna password, ma
**si entra con un clic**, non da soli. **Entra con un altro nome** porta ai
campi di nome e password; **Torna a …** riporta al tuo account.

Come per Active Directory, **l'utente dev'essere stato aggiunto** da un
amministratore con **Aggiungi dal dominio**, e i gruppi sono quelli del dominio
legati nella matrice. Chi non è stato aggiunto si sente rispondere come a una
password sbagliata.

> **Non ancora provato su una macchina vera.** Kerberos non è mai stato eseguito
> su un computer Windows dentro un dominio vero, né su un Mac: sul Mac il
> programma si costruisce, ma nessuno l'ha ancora fatto entrare così.

## Più modi insieme

I modi si accendono anche insieme, e il dialogo mostra quelli accesi: per
esempio **Entra con Keycloak**, «oppure», e i campi di nome e password.

Due regole valgono sempre:

- **la password degli amministratori funziona sempre**, anche quando fra i modi
  la password non c'è: è l'uscita d'emergenza quando il dominio o il fornitore
  non rispondono. In quel caso, però, vale **solo per gli amministratori**;
- **chi entra dal dominio, da un fornitore o con Kerberos non diventa
  amministratore.** Per esserlo serve un utente con la password del servizio.

## La sessione

Entrati, la sessione resta **su questo computer**, nel portachiavi del sistema
(Gestione credenziali su Windows, Portachiavi su Mac) e non in
`impostazioni.json`. **Riaprendo il programma non serve rientrare**, finché la
sessione è viva.

| | finisce |
|---|---|
| con la password del servizio | dopo **trenta giorni senza usarla**: ogni gesto la rinnova |
| dal dominio, da un fornitore, con Kerberos | **dodici ore dopo l'accesso**, anche se la stai usando |

Finisce prima se chi gestisce il servizio la chiude da **Utenti e gruppi**, se
la tua password viene reimpostata o se il tuo utente viene disattivato. Allora il
dialogo si riapre da solo. Ogni computer ha la sua sessione: entrare di nuovo
dallo stesso computer sostituisce quella di prima.

**Dopo cinque tentativi sbagliati di fila** sullo stesso nome bisogna aspettare:
**un minuto** con la password del servizio, **un quarto d'ora** con un nome del
dominio.

**Il catalogo di questo computer resta senza accesso**: i nomi e le password
valgono solo sul servizio.

### Uscire e cambiare la password

Il tuo nome, nella barra in alto, apre un menu. Dentro ci sono:

- **Esci**, che chiude la sessione sul servizio, la dimentica da questo computer
  — anche se il servizio non risponde — e riapre il dialogo;
- **Cambia la password…**, solo per chi entra con la password del servizio:
  chiede la **Password di adesso** e la **Password nuova**. Le tue sessioni
  sugli altri computer si chiudono, e lì rientri con quella nuova; questa resta
  aperta. La password del dominio, invece, si cambia nel dominio.

## Il blocco `accesso` di `servizio.json`

Questa parte è per chi gestisce il servizio. I modi si accendono nel blocco
`accesso` di `servizio.json`, nella cartella dati del servizio — dove sta su
ogni sistema lo dice [Installare il servizio](Installare-il-servizio.md#il-file-serviziojson).
**Gli installer non lo scrivono**: di partenza manca, e vale la sola password.
Va scritto a mano, e dopo il servizio va riavviato.

`modi` elenca i modi accesi, fra `password`, `ldap`, `oidc` e `kerberos`; senza,
vale `["password"]`. Ogni modo acceso vuole il suo blocco, e un blocco senza il
suo modo si rifiuta. **Una chiave che il servizio non conosce fa rifiutare il
file**: il servizio non parte e il registro dice quale, così una chiave scritta
male non passa in silenzio.

Active Directory, accanto alla password:

```json
{
  "ascolta": "0.0.0.0:7878",
  "accesso": {
    "modi": ["password", "ldap"],
    "ldap": {
      "indirizzo": "ldaps://dc1.biblio.local:636",
      "dominio": "BIBLIO",
      "ca": "ca-dominio.pem"
    }
  }
}
```

- `indirizzo` comincia sempre con `ldaps://`: in chiaro il servizio non parla al
  dominio;
- `dominio` è il nome breve del dominio, quello che si scrive davanti al nome;
- `ca` è il file PEM col certificato che ha firmato quello del controller di
  dominio, nella stessa cartella di `servizio.json`;
- `account_di_servizio` e `password_di_servizio` sono facoltativi: un account
  con cui il servizio cerca gli utenti nel dominio. Kerberos li vuole.

Un fornitore OIDC:

```json
{
  "accesso": {
    "modi": ["password", "oidc"],
    "oidc": {
      "issuer": "https://keycloak.biblio.local/realms/biblioteca",
      "client_id": "gestionale-libreria"
    }
  }
}
```

- `issuer` è l'indirizzo del fornitore, in `https://`;
- `client_id` è il nome con cui il fornitore conosce il servizio;
- facoltativi: `segreto` (se il fornitore lo chiede), `ca` (se il certificato
  del fornitore non è di un'autorità pubblica), `claim_dei_gruppi` (dove il
  fornitore scrive i gruppi; di partenza `groups`) e `fornitore`, il nome che il
  pulsante mostra (di partenza `Keycloak`).

Kerberos, che vuole anche il blocco `ldap` con l'account di servizio:

```json
{
  "accesso": {
    "modi": ["password", "kerberos"],
    "ldap": {
      "indirizzo": "ldaps://dc1.biblio.local:636",
      "dominio": "BIBLIO",
      "ca": "ca-dominio.pem",
      "account_di_servizio": "svc-gestionale",
      "password_di_servizio": "la-password-dell-account"
    },
    "kerberos": {
      "realm": "BIBLIO.LOCAL",
      "keytab": "biblioteca.keytab"
    }
  }
}
```

- `realm` è il realm Kerberos del dominio;
- `keytab` è il file con le chiavi del servizio; senza, vale quello del sistema.
  Su Windows, senza keytab, i ticket li verifica Windows stesso;
- `principale` è facoltativo: senza, vale ogni chiave del keytab.

I segreti possono restare fuori dal file, in tre variabili d'ambiente che,
quando ci sono, vincono su `servizio.json`:

| | |
|---|---|
| `GESTIONALE_LIBRERIA_SEGRETO_OIDC` | il `segreto` del fornitore OIDC |
| `GESTIONALE_LIBRERIA_PASSWORD_DI_SERVIZIO` | la `password_di_servizio` del dominio |
| `GESTIONALE_LIBRERIA_KEYTAB` | il percorso del `keytab` |

All'avvio il registro del servizio dice con quali modi si entra, e se la
password vale solo per gli amministratori.

### Provare prima di riavviare

L'opzione `--prova` legge `servizio.json`, prova quello che c'è scritto e dice
in una riga com'è andata, senza mettersi a servire:

- il database, se c'è;
- con il blocco `ldap`, che il dominio risponda in LDAPS — e, se c'è l'account
  di servizio, che il dominio lo accetti;
- con il blocco `oidc`, che il fornitore risponda e si presenti con l'`issuer`
  scritto nel file;
- con il blocco `kerberos`, che il keytab si legga e porti la chiave del
  servizio per quel realm.

I comandi per lanciarla su ogni sistema stanno in
[Installare il servizio](Installare-il-servizio.md#il-file-serviziojson).
