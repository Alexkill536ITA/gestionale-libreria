**Italiano** · [English](../en/Installing-the-service.md)

# Installare il servizio

Il **servizio della biblioteca** è un programma a parte, senza finestra, che
tiene il catalogo su un computer della biblioteca e risponde agli altri
computer della rete, dove gira l'app. Ognuno entra con il suo nome e la sua
password, e chi gestisce il servizio decide cosa può fare. Come si collega
l'app lo racconta [Dove stanno i dati](Dove-stanno-i-dati.md#col-servizio-della-biblioteca);
questa pagina dice come si mette in piedi il servizio.

Se il catalogo lo usi da solo, il servizio non ti serve: basta l'app,
[installata come sempre](Installazione.md).

## Prima di cominciare

- **Un computer che resta acceso**, perché gli altri lo raggiungano: un PC
  Windows a 64 bit, un Mac (Intel o Apple Silicon), un server Linux con
  systemd (amd64 o arm64), oppure Docker. Sul computer del servizio l'app non
  serve.
- **La stessa versione dell'app.** Il servizio e l'app si parlano solo se sono
  dello stesso rilascio: un'app più nuova o più vecchia del servizio si sente
  dire «Il servizio è alla versione …, questo programma a un'altra». Quando
  aggiorni l'una, aggiorna anche l'altro.
- **Dove tenere il catalogo.** Di partenza il servizio lo tiene in un file
  nella sua cartella dati, e non serve installare nient'altro. Se la biblioteca
  ha già un database — **PostgreSQL**, **MySQL**, **SQL Server** o **MongoDB**
  avviato come replica set — il catalogo può stare lì: le regole sono quelle di
  [Il catalogo su un server](Il-catalogo-su-un-server.md).
- **La porta 7878** raggiungibile dagli altri computer. È quella di partenza, e
  si cambia.

I file stanno nella [pagina dell'ultima
versione](https://github.com/alexkill536ita/gestionale-libreria/releases/latest),
accanto a quelli dell'app.

## Su Windows

Il file è `Gestionale Libreria Servizio_0.7.5_x64-setup.exe`. Chiede i permessi
di amministratore, perché installa un servizio di Windows; e come per l'app,
**SmartScreen** avvisa che il programma non è firmato: **Ulteriori
informazioni** → **Esegui comunque**.

All'avvio l'installazione chiede la lingua, italiano o inglese, e propone
quella di Windows. Le pagine sono quattro:

1. **La cartella del programma**, di partenza `C:\Program Files\Gestionale
   Libreria Servizio`.
2. **Configurazione del servizio.** L'**Indirizzo di ascolto** proposto è
   `0.0.0.0:7878`, che risponde a tutta la rete della biblioteca;
   `127.0.0.1:7878` risponde solo a questo computer. Sotto si sceglie **Dove sta
   il catalogo**: **Su questo computer**, un file nella cartella dati con le
   copertine accanto, oppure **Su un database**.
3. Solo con **Su un database**, altre due pagine: **Il database del catalogo** —
   motore, host, porta, nome del database, utente, password e **Collegamento
   cifrato (TLS)**, con **Prova il collegamento** per sapere subito se risponde —
   e **Le copertine**: **Dentro il database**, **In una cartella** o **In un
   archivio S3**. La cartella proposta è `covers` nella cartella dati, e se ne
   può scegliere un'altra. Una cartella di rete deve dare il permesso di scrivere
   all'account `NT SERVICE\GestionaleLibreria`, o le copertine non si salvano.
4. **Il servizio è partito.** L'ultima pagina mostra l'indirizzo da scrivere
   nell'app — `https://NOME-DEL-COMPUTER:7878`, con gli indirizzi IP di questo
   computer — il **Codice di configurazione** e l'**Impronta del certificato**,
   ciascuno col suo pulsante **Copia**. Tienili a portata: servono al primo
   collegamento.

Cosa resta sul computer:

| | |
|---|---|
| il servizio di Windows | `GestionaleLibreria` («Gestionale Libreria - Servizio» in **Servizi**), che parte da solo con il computer anche se nessuno è entrato, e gira con l'account `NT SERVICE\GestionaleLibreria` |
| la cartella dati | `C:\ProgramData\Gestionale Libreria\servizio`, aperta solo a SYSTEM, agli amministratori e al servizio: dentro ci sono `servizio.json`, il catalogo, le copertine, gli utenti, il certificato e il registro `servizio.log` |
| il firewall | una regola «Gestionale Libreria Servizio» che apre la porta sulle reti **Private** e di **Dominio**, non su quelle pubbliche |

Se il servizio non parte, l'ultima pagina lo dice e mostra il registro, con
**Apri il registro**.

## Su un Mac

Il file è `Gestionale Libreria Servizio_0.7.5_universal.pkg`, uno solo per i Mac
Intel e per quelli con Apple Silicon. Come l'app **non è firmato**: macOS dice
che non si può verificare, e si passa da **Impostazioni di sistema → Privacy e
sicurezza → Apri comunque**.

Il pacchetto:

- mette il programma in `/usr/local/bin/gestionale-libreria-servizio`;
- crea l'utente di sistema `_gestionalelibreria`, nascosto e senza accesso, che
  è il solo a leggere la cartella dati;
- tiene i dati in `/Library/Application Support/Gestionale Libreria/servizio`;
- avvia il servizio subito e a ogni accensione del Mac, come LaunchDaemon
  `it.alexkill536ita.gestionale-libreria.servizio`, in ascolto su
  `0.0.0.0:7878`.

Il catalogo parte in un file nella cartella dati; per tenerlo su un database si
modifica `servizio.json`, come dice [più sotto](#il-file-serviziojson). L'ultima pagina
dell'installazione riassume i comandi che servono, gli stessi di qui.

Il **codice di configurazione**, dal Terminale:

```
sudo cat "/Library/Application Support/Gestionale Libreria/servizio/codice-di-configurazione.txt"
```

L'**impronta del certificato**:

```
sudo -u _gestionalelibreria /usr/local/bin/gestionale-libreria-servizio --impronta
```

L'**indirizzo** da scrivere nell'app è `https://NOME.local:7878`, dove `NOME` è
quello che risponde `scutil --get LocalHostName`; va bene anche l'indirizzo IP
del Mac.

Se il **firewall di macOS** è acceso, le connessioni in arrivo vanno consentite
a mano, perché il servizio non ha una finestra da cui chiederlo:

```
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add /usr/local/bin/gestionale-libreria-servizio
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp /usr/local/bin/gestionale-libreria-servizio
```

Dopo aver cambiato `servizio.json` il servizio si riavvia con:

```
sudo launchctl kickstart -k system/it.alexkill536ita.gestionale-libreria.servizio
```

## Su Linux

Su **Debian e Ubuntu** c'è un pacchetto `.deb`:
`gestionale-libreria-servizio_0.7.5_amd64.deb` per i PC e
`gestionale-libreria-servizio_0.7.5_arm64.deb` per i server ARM (un Raspberry Pi
a 64 bit, per esempio).

```
sudo apt install ./gestionale-libreria-servizio_0.7.5_amd64.deb
```

Il pacchetto crea l'utente di sistema `gestionale-libreria`, la cartella dati
`/var/lib/gestionale-libreria` aperta solo a lui, un `servizio.json` in ascolto
su `0.0.0.0:7878`, e accende l'unità systemd `gestionale-libreria-servizio`, che
parte da sola a ogni avvio. **Il firewall non lo tocca**: se c'è, la porta
`7878/tcp` va aperta a mano.

Per le **altre distribuzioni con systemd** c'è un archivio,
`gestionale-libreria-servizio_0.7.5_linux-x86_64.tar.gz` o
`gestionale-libreria-servizio_0.7.5_linux-aarch64.tar.gz`. Dentro ci sono il
programma, l'unità systemd e `LEGGIMI.txt` (in inglese `README.txt`), con i
passi da fare a mano: sono gli stessi che il `.deb` fa da solo. Il programma
vuole OpenSSL 3 e una glibc almeno come quella di Ubuntu 22.04.

I comandi che servono dopo:

```
sudo cat /var/lib/gestionale-libreria/codice-di-configurazione.txt
sudo -u gestionale-libreria gestionale-libreria-servizio --impronta
sudo systemctl restart gestionale-libreria-servizio
journalctl -u gestionale-libreria-servizio
```

I comandi del programma si danno sempre **come l'utente del servizio**
(`sudo -u gestionale-libreria …`): lanciati da root, i file che scrivono nella
cartella dati sarebbero di root, e il servizio non li potrebbe aprire.

## Con Docker

Un'immagine pronta non c'è: c'è questo `Dockerfile`, che scarica l'archivio
Linux della versione dal rilascio. Copialo in una cartella vuota.

```dockerfile
FROM debian:bookworm-slim

ARG VERSIONE=0.7.5
ARG ARCH=x86_64

RUN apt-get update \
 && apt-get install -y --no-install-recommends ca-certificates curl libssl3 libgssapi-krb5-2 \
 && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL "https://github.com/alexkill536ita/gestionale-libreria/releases/download/v${VERSIONE}/gestionale-libreria-servizio_${VERSIONE}_linux-${ARCH}.tar.gz" \
      | tar -xz -C /tmp \
 && install -m 0755 "/tmp/gestionale-libreria-servizio_${VERSIONE}_linux-${ARCH}/gestionale-libreria-servizio" /usr/local/bin/ \
 && rm -rf /tmp/gestionale-libreria-servizio_*

RUN useradd --system --user-group --no-create-home \
      --home-dir /var/lib/gestionale-libreria --shell /usr/sbin/nologin gestionale-libreria \
 && install -d -m 0750 -o gestionale-libreria -g gestionale-libreria /var/lib/gestionale-libreria

VOLUME /var/lib/gestionale-libreria
ENV GESTIONALE_LIBRERIA_ASCOLTA=0.0.0.0:7878
EXPOSE 7878
USER gestionale-libreria
ENTRYPOINT ["gestionale-libreria-servizio"]
```

Su un server ARM l'archivio è un altro: si costruisce con
`--build-arg ARCH=aarch64`.

```
docker build -t gestionale-libreria-servizio .
docker run -d --name biblioteca --restart unless-stopped --stop-timeout 15 \
  -v biblioteca-dati:/var/lib/gestionale-libreria \
  -p 7878:7878 gestionale-libreria-servizio
```

I dati stanno nel **volume** `biblioteca-dati`, e sopravvivono al contenitore:
catalogo, utenti e soprattutto il certificato, la cui impronta i computer
collegati ricordano. Usa un volume con nome e non una cartella dell'host: il
servizio gira con un utente suo, e una cartella dell'host di solito non lo
lascerebbe scrivere. `--stop-timeout 15` lascia al servizio il tempo di
finire quello che sta facendo prima di fermarsi: senza, Docker lo ferma di
forza dopo pochi secondi.

Codice di configurazione e impronta:

```
docker exec biblioteca cat /var/lib/gestionale-libreria/codice-di-configurazione.txt
docker exec biblioteca gestionale-libreria-servizio --impronta
```

Li stampa anche `docker logs biblioteca`, all'avvio.

L'indirizzo da scrivere nell'app è quello del computer che fa girare Docker,
con la porta pubblicata: `https://192.168.1.20:7878`, per esempio.

Senza `servizio.json` il catalogo sta in un file nel volume. Per un database,
il file si scrive dentro il volume e si riavvia il contenitore:

```
docker exec -i biblioteca sh -c 'cat > /var/lib/gestionale-libreria/servizio.json' < servizio.json
docker restart biblioteca
```

La password del database può restare fuori dal file, in una variabile:
`-e GESTIONALE_LIBRERIA_PASSWORD=…` su `docker run`.

## Il file `servizio.json`

Il servizio legge la sua configurazione da `servizio.json`, nella cartella dati.
Le chiavi sono tre:

| | |
|---|---|
| `ascolta` | dove risponde: `0.0.0.0:7878` per tutta la rete, `127.0.0.1:7878` solo per quel computer. Senza, è il secondo |
| `database` | dove sta il catalogo. Senza, è un file nella cartella dati, con le copertine accanto |
| `dati` | un'altra cartella dati; di solito non serve |

Ecco un catalogo su un PostgreSQL della biblioteca, con le copertine in un
archivio S3:

```json
{
  "ascolta": "0.0.0.0:7878",
  "database": {
    "motore": "postgres",
    "host": "db.biblioteca.lan",
    "porta": 5432,
    "database": "libreria",
    "utente": "libreria",
    "password": "la-password-del-database",
    "tls": true,
    "copertine": "in_un_archivio",
    "archivio_indirizzo": "https://s3.eu-central-1.amazonaws.com",
    "archivio_contenitore": "copertine-biblioteca",
    "archivio_regione": "eu-central-1",
    "archivio_chiave": "la-chiave-d-accesso",
    "archivio_segreto": "il-segreto"
  }
}
```

- `motore` è uno fra `postgres`, `mysql`, `sqlserver` e `mongodb`. Su MongoDB
  c'è in più `database_autenticazione`, il database dove l'utente è definito
  (di partenza `admin`).
- `copertine` è `nel_database`, `in_una_cartella` — con `cartella_copertine`,
  il percorso visto dal computer del servizio — oppure `in_un_archivio`, con i
  cinque campi `archivio_*`; la regione si può omettere.
- Il posto delle copertine vale **quando il catalogo non ne ha ancora uno**: un
  catalogo che ha già deciso dove stanno le sue copertine se lo ricorda, e chiave
  e segreto dell'archivio si leggono sempre da qui. Se il file ne nomina un
  altro, all'avvio `servizio.log` lo dice e le copertine restano dove dice il
  catalogo.
- **La password** può stare nel file, che solo il servizio e gli amministratori
  leggono, oppure nella variabile d'ambiente `GESTIONALE_LIBRERIA_PASSWORD`.
  Anche l'indirizzo di ascolto si può dare con una variabile,
  `GESTIONALE_LIBRERIA_ASCOLTA`, che vince sul file.

Un database vuoto va bene: il servizio ci installa il catalogo da sé al primo
avvio. Per sapere se il collegamento funziona **prima** di riavviare il
servizio, c'è l'opzione `--prova`, che prova il database di `servizio.json`,
dice in una riga com'è andata ed esce:

```
sudo -u gestionale-libreria gestionale-libreria-servizio --prova
```

(su Windows, da un PowerShell aperto come amministratore:
`& "C:\Program Files\Gestionale Libreria Servizio\gestionale-libreria-servizio.exe" --prova`).

Dopo ogni modifica il servizio va **riavviato**: da **Servizi** su Windows, con
`launchctl kickstart -k` su un Mac, con `systemctl restart` su Linux, con
`docker restart` su Docker.

## Collegare l'app

Su ogni computer della biblioteca, nell'app:

1. **Impostazioni → Database**, nel gruppo **In una biblioteca**: **Col
   servizio della biblioteca**.
2. Nel campo **Indirizzo** scrivi quello del servizio, sempre con `https://` e
   la porta: `https://192.168.1.20:7878`.
3. La prima volta l'app mostra l'**Impronta del servizio**. Confrontala con
   quella dell'installazione, o con quella che stampa `--impronta`: se sono
   uguali, premi **Mi fido**. Se non lo sono, non fidarti — qualcuno sta in mezzo
   — e se l'app dice che «un programma di questo computer legge il
   collegamento», di solito è un antivirus con la scansione HTTPS accesa.
4. Il **primo** computer che si collega crea il primo amministratore: il dialogo
   chiede il **Codice di configurazione**, poi un nome e una password. Il codice
   vale una volta sola. Gli altri computer entrano con il loro nome e la loro
   password.

I dettagli — l'impronta che cambia, la sessione, cosa si fa col catalogo sul
servizio — stanno in [Dove stanno i dati](Dove-stanno-i-dati.md#col-servizio-della-biblioteca).

## Aggiornare

**Si installa sopra**, con il file della versione nuova, e la configurazione
resta com'è.

- **Windows**: l'installazione nuova riconosce quella di prima, salta le pagine
  della configurazione e non tocca `servizio.json`.
- **Mac**: si apre il `.pkg` nuovo; i dati e `servizio.json` restano.
- **Debian e Ubuntu**: lo stesso `sudo apt install`, col `.deb` nuovo; il
  servizio riparte da solo.
- **Archivio Linux**: si ferma il servizio, si sostituisce il programma in
  `/usr/bin` e lo si riavvia.
- **Docker**: si cambia `ARG VERSIONE` nel `Dockerfile` (o si passa
  `--build-arg VERSIONE=…`), si ricostruisce l'immagine e si ricrea il
  contenitore con lo **stesso volume**.

Ricorda di aggiornare **anche l'app** sui computer della biblioteca, o non si
collegano più.

## Disinstallare

La cartella dati si cancella solo se lo chiedi: altrimenti catalogo, utenti e
certificato restano, e un servizio reinstallato li ritrova com'erano.

- **Windows**: da **Impostazioni → App → App installate**, voce «Gestionale
  Libreria - Servizio». Si tolgono il servizio, la regola del firewall e il
  programma, e prima di cominciare ti chiede se cancellare anche
  `C:\ProgramData\Gestionale Libreria\servizio`; la risposta proposta è «No».
  Cancellata non si recupera, e i computer collegati dovranno confermare
  l'impronta di un servizio nuovo. Se le copertine stanno in una cartella
  scelta fuori da lì, la domanda la nomina e il «Sì» cancella anche le
  immagini che contiene; sottocartelle e altri file restano, e la cartella se
  ne va solo se rimane vuota. Una disinstallazione silenziosa (`/S`) non
  cancella mai niente di tutto questo.
- **Mac**:

  ```
  sudo /usr/local/share/gestionale-libreria-servizio/disinstalla.sh
  ```

  Alla fine dice anche come togliere la cartella dati e l'utente
  `_gestionalelibreria`.
- **Debian e Ubuntu**: `sudo apt remove gestionale-libreria-servizio`. Per
  togliere davvero dati e utente:
  `sudo rm -rf /var/lib/gestionale-libreria` e
  `sudo deluser --system gestionale-libreria`.
- **Archivio Linux**: i passi stanno in fondo a `LEGGIMI.txt`.
- **Docker**: `docker rm -f biblioteca`; i dati restano nel volume finché non
  lo togli con `docker volume rm biblioteca-dati`.

## Il codice perso, o la password dell'amministratore

Il codice di configurazione nasce a ogni avvio **finché non c'è nessun utente**.
Se l'amministratore ha perso la password, un codice nuovo si fa nascere sulla
macchina del servizio con l'opzione `--nuovo-codice`: il programma lo scrive in
`codice-di-configurazione.txt`, lo stampa ed esce, senza fermare il servizio
che sta girando.

```
sudo -u gestionale-libreria gestionale-libreria-servizio --nuovo-codice                                  # Linux
sudo -u _gestionalelibreria /usr/local/bin/gestionale-libreria-servizio --nuovo-codice                   # Mac
docker exec biblioteca gestionale-libreria-servizio --nuovo-codice                                       # Docker
```

Su Windows, da un PowerShell aperto come amministratore:

```
& "C:\Program Files\Gestionale Libreria Servizio\gestionale-libreria-servizio.exe" --nuovo-codice
```

Poi, nell'app, si crea l'amministratore con quel codice: con il **nome che
c'era** torna amministratore con la password nuova, con un nome nuovo nasce un
amministratore in più.

## Se non parte

Il servizio scrive quello che fa in `servizio.log`, nella sua cartella dati, e
all'avvio ci scrive anche l'impronta.

| | |
|---|---|
| Windows | `C:\ProgramData\Gestionale Libreria\servizio\servizio.log`, da aprire come amministratore |
| Mac | `servizio.log` nella cartella dati; quello che dice prima di aprirla — un `servizio.json` che non si legge, per esempio — sta in `/Library/Logs/Gestionale Libreria/servizio.log` |
| Linux | `journalctl -u gestionale-libreria-servizio`, e `servizio.log` in `/var/lib/gestionale-libreria` |
| Docker | `docker logs biblioteca` |

Le cause più comuni:

- **il database non risponde**, o utente e password sono sbagliati: `--prova` lo
  dice senza avviare niente;
- **la porta è già usata** da un altro programma: cambia `ascolta` in
  `servizio.json`;
- **`servizio.json` non si legge**: una virgola di troppo, o una chiave scritta
  male;
- **gli altri computer non lo raggiungono**, ma da quello del servizio sì: è il
  firewall, oppure `ascolta` dice `127.0.0.1`.
