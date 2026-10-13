<div align="center">

<img src="immagini/logo.png" alt="" width="96" height="96">

# Gestionale Libreria

**Il catalogo della tua libreria di carta.**
Inquadri il codice a barre, e il libro si cataloga da solo.

[![Tauri](https://img.shields.io/badge/Tauri-2-24C8DB?style=flat-square&logo=tauri&logoColor=white)](https://tauri.app)
[![Rust](https://img.shields.io/badge/Rust-2021-CE422B?style=flat-square&logo=rust&logoColor=white)](https://www.rust-lang.org)
[![React](https://img.shields.io/badge/React-19-087EA4?style=flat-square&logo=react&logoColor=white)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind](https://img.shields.io/badge/Tailwind-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Windows](https://img.shields.io/badge/Windows-10%20e%2011-0078D4?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgODggODgiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgaGVpZ2h0PSI4OCIgd2lkdGg9Ijg4Ij48cGF0aCBkPSJtMCAxMi40MDIgMzUuNjg3LTQuODYuMDE2IDM0LjQyMy0zNS42Ny4yMDN6bTM1LjY3IDMzLjUyOS4wMjggMzQuNDUzTC4wMjggNzUuNDguMDI2IDQ1Ljd6bTQuMzI2LTM5LjAyNUw4Ny4zMTQgMHY0MS41MjdsLTQ3LjMxOC4zNzZ6bTQ3LjMyOSAzOS4zNDktLjAxMSA0MS4zNC00Ny4zMTgtNi42NzgtLjA2Ni0zNC43Mzl6IiBmaWxsPSIjMDBhZGVmIi8+PC9zdmc+)](#installazione)
[![macOS](https://img.shields.io/badge/macOS-universale-8E8E93?style=flat-square&logo=apple&logoColor=white)](#macos)

[**Guida d'uso**](wiki/it/Home.md) · [**User guide**](wiki/en/Home.md) · [Installazione](#installazione)
<img src="wiki/it/immagini/catalogo.png" alt="Il catalogo" width="820">

</div>

---

## Che cos'è

Un catalogo di libri **di carta**, per Windows e macOS. Chi lo usa da solo non
crea nessun account: di partenza sta su questo computer e funziona **senza
rete** — tranne quando vai a cercare i dati di un libro, che arrivano da cinque
cataloghi pubblici. Se vuoi, il catalogo può stare invece **su un tuo
database**: PostgreSQL, MySQL, SQL Server o MongoDB, con le copertine dentro il
database, in una cartella o in un archivio S3.

E se a usarlo siete in tanti c'è la terza strada, **il servizio della
biblioteca**: un programma a parte che tiene un catalogo solo per tutti i
computer della rete. Lì ognuno entra col suo account — con una password, con
Active Directory, con un fornitore OIDC come Keycloak o con Kerberos — e fa
quello che i suoi permessi gli concedono. Al primo avvio una guida chiede quale
delle strade vuoi, e si cambia dopo.

Non è una libreria digitale e non ti manda notifiche: tiene il conto di quello
che hai sugli scaffali, di dove sta, di cosa manca a una serie, di cosa vuoi
ancora comprare e di chi non ti ha ancora ridato quel volume.

Dal 1° settembre 2026 ogni release porta anche un **DMG universale per macOS**,
che il CI costruisce accanto all'installer di Windows: è stato aperto su un Mac e
funziona. Come si installa sta in [macOS](#macos).

<table>
<tr>
<td width="50%" valign="top">

### 📷 Cataloga con la webcam
Inquadri il codice a barre, l'ISBN si scrive da solo e parte la ricerca.
Con «Salva e aggiungi un altro» smaltisci una pila senza mai riaprire nulla.

</td>
<td width="50%" valign="top">

### 🔎 Cinque fonti, una scheda
OpenLibrary, Google Books, OPAC SBN e NiceBooks interrogate insieme; AniList per
il manga. Dove non sono d'accordo, scegli tu con un clic.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 📚 Le serie, coi buchi in vista
`mancano 2, 4–20`: ogni serie è una riga che si apre su una griglia a venti
colonne, dove i volumi che non hai sono tratteggiati. E una serie impara tag,
genere, editore e collana dai suoi volumi, per poi passarli al prossimo che
aggiungi. Dalla pagina di un editore, un clic su un'opera ne apre la scheda:
volumi, costo medio, spesa, pagine, e dove i volumi non dicono la stessa cosa.

</td>
<td width="50%" valign="top">

### ⚡ Cerca e perdona i refusi
Ricerca full-text mentre digiti. Se scrivi `camileri`, ti mostra Camilleri —
e undici filtri per genere, autore, editore, posizione, tag, anno.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🤝 Sai a chi l'hai prestato
Chi ha quale libro e da quanto, con la striscia di quello che non è sulla
mensola. Il libro che torna lo riconosci col codice a barre — e finché è fuori,
non si può eliminare per sbaglio.

</td>
<td width="50%" valign="top">

### 💾 Backup quando lo chiedi tu
Un archivio con catalogo **e** copertine, e niente che parta da solo. Ultime
sette copie, e un ripristino che nomina i due conteggi prima di sostituire.
Nell'altro verso, un foglio CSV entra nel catalogo dopo averti detto quanti
libri porta, quanti ci sono già e quali righe non si leggono.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🌍 Due lingue, tema chiaro e scuro
Italiano e inglese, cambio istantaneo, errori compresi.
I tuoi dati restano scritti come li hai inseriti.

</td>
<td width="50%" valign="top">

### 🔔 Ti dice se esce una versione nuova
Un controllo all'avvio, il changelog nell'avviso e «Salta questa versione» se
non ti interessa. **Non scarica e non installa niente da sé**: apre la pagina
della release, il resto lo decidi tu.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🗂 I nomi del catalogo li correggi tu
Sei dizionari — tag, autori, generi, collane, posizioni e lingue — che nascono
da soli catalogando. Si rinominano, si uniscono quando sono due nomi della
stessa cosa — `アネコユサギ` e `Yusagi Aneko` — e si tolgono quando non li usa
più nessuno. Sposti uno scaffale, e la posizione la riscrivi in un gesto solo.

</td>
<td width="50%" valign="top">

### 🕰 Lo storico, se lo vuoi
Nasce spento. Acceso, registra cosa hai cambiato e quando, con il `campo ·
vecchio → nuovo` di ogni modifica e la storia completa di ogni libro.
**Spegnerlo cancella quello che ha registrato**, e prima te lo chiede. Sul
servizio della biblioteca dice anche chi.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🛒 Da acquistare
La lista dei volumi che non hai ancora: un ISBN o un titolo, e la cascata
riempie il resto. Accanto, il resoconto di quanto costa finire quello che stai
leggendo. Arrivato il pacco, «Aggiungi a catalogo» li porta dentro con tutto
quello che si sapeva di loro.

</td>
<td width="50%" valign="top">

### 📖 Da leggere, in lettura, letto, lasciato
Quattro stati, e il quarto è il libro cominciato e messo da parte. Si cambiano
con un clic sulla cella «Letto» del catalogo, senza aprire il modulo.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🏛 Il servizio della biblioteca
Un catalogo solo per tutti i computer della rete, e ognuno entra col suo
account: password, Active Directory, OIDC o Kerberos. Gruppi e permessi decidono
chi fa cosa. Chi apre un libro lo **prenota**, e gli altri lo vedono cambiare in
diretta; ognuno tiene **le sue letture**, che nessun altro vede.

</td>
<td width="50%" valign="top">

### 🔒 Nessuna telemetria
Il catalogo sta su questo computer, sul tuo database o sul servizio della tua
biblioteca, e da nessun'altra parte. Le altre richieste in rete sono quelle che
chiedi tu: i dati di un libro, e l'elenco delle release.

</td>
</tr>
</table>

## Come si presenta

<table>
<tr>
<td width="50%"><img src="wiki/it/immagini/cascata-riempito.png" alt="La cascata dei metadati"><br><sub><b>Una scheda riempita dalle fonti</b> — la copertina scende da sola, e quando più fonti ne hanno una si sceglie da una fila di miniature; sotto ogni campo conteso c'è la pastiglia con le alternative.</sub></td>
<td width="50%"><img src="wiki/it/immagini/serie.png" alt="La vista delle serie"><br><sub><b>Le serie</b> — quanti volumi hai su quanti, quali mancano, e la griglia a venti colonne che si apre sotto ogni serie.</sub></td>
</tr>
<tr>
<td width="50%"><img src="wiki/it/immagini/filtri-pannello.png" alt="Il pannello dei filtri"><br><sub><b>I filtri</b> — undici, e dieci con i conteggi, così sai in anticipo quanti libri resteranno.</sub></td>
<td width="50%"><img src="wiki/it/immagini/anilist-riempito.png" alt="Un manga da AniList"><br><sub><b>Il manga da AniList</b> — autore e disegnatore distinti, il totale dei volumi, i tag proposti.</sub></td>
</tr>
<tr>
<td width="50%"><img src="wiki/it/immagini/editori.png" alt="La pagina di un editore"><br><sub><b>Gli editori</b> — un editore per volta: le sue opere in un carosello, le altre grafie con cui si presenta, e quattro grafici nella sua tinta.</sub></td>
<td width="50%"><img src="wiki/it/immagini/scanner.png" alt="Lo scanner del codice a barre"><br><sub><b>Lo scanner</b> — mirino nel modulo, decodifica in WebAssembly, tendina per scegliere la fotocamera.</sub></td>
</tr>
<tr>
<td width="50%"><img src="wiki/it/immagini/impostazioni-preferenze.png" alt="Le impostazioni"><br><sub><b>Le impostazioni</b> — il binario non elenca le sezioni, le riassume: sotto ogni voce c'è il valore di adesso.</sub></td>
<td width="50%"><img src="wiki/it/immagini/modulo-scorrimento.png" alt="Le frecce del modulo"><br><sub><b>Scorrere il catalogo</b> — dal modulo di un libro si passa al successivo senza chiudere, anche oltre il bordo della pagina.</sub></td>
</tr>
<tr>
<td width="50%"><img src="wiki/it/immagini/acquisti.png" alt="La lista da acquistare"><br><sub><b>Da acquistare</b> — i volumi che non hai ancora, con la fonte da cui vengono, e a destra il resoconto di quanto costano.</sub></td>
<td width="50%"><img src="wiki/it/immagini/servizio-accesso.png" alt="L'ingresso nel servizio"><br><sub><b>Il servizio della biblioteca</b> — si entra col proprio nome, e l'impronta del servizio è confermata prima di mandargli una password.</sub></td>
</tr>
</table>

## Da dove vengono i dati

| | Fonte | Che cosa porta | Chiave |
|:--:|---|---|:--:|
| 1 | **OpenLibrary** | comanda la cascata, e porta la copertina | — |
| 2 | **Google Books** | i dati dell'editoria che le altre non hanno | serve |
| 3 | **OPAC SBN** | il catalogo delle biblioteche italiane, riempie i buchi | — |
| 4 | **NiceBooks** | la copertura italiana, manga compresi, con la sua copertina | — |
| ★ | **AniList** | manga: autore e disegnatore distinti, serie, copertina | — |

Le prime quattro partono **insieme**, non in fila, ma l'ordine conta: comanda la
prima della cascata — OpenLibrary, poi Google Books, SBN e NiceBooks — e le
altre riempiono solo i campi che ha lasciato vuoti. AniList sta fuori dalla cascata
perché non conosce gli ISBN — cataloga opere, non edizioni — quindi compare solo
nella ricerca per titolo, dove scegli tu.

## Installazione

### Windows

Serve `Gestionale Libreria_0.8.0_x64-setup.exe`, dalla [pagina dell'ultima
versione](https://github.com/alexkill536ita/gestionale-libreria/releases/latest).

Installa **per il solo utente corrente**, quindi non chiede l'amministratore, e
il componente WebView2 è già dentro: nessun download durante l'installazione.

> [!NOTE]
> Al primo avvio Windows mostra SmartScreen: **il programma non è firmato**, e un
> certificato costa un canone annuo senza nemmeno spegnere l'avviso da solo.
> **Ulteriori informazioni → Esegui comunque**.

Di partenza i tuoi dati vivono in
`%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\` — catalogo, copertine,
backup, impostazioni — e **la disinstallazione non li cancella**. Il catalogo si
può spostare in un'altra cartella o su un server; le impostazioni restano lì.

### macOS

`Gestionale Libreria_0.8.0_universal.dmg`, dalla [stessa
pagina](https://github.com/alexkill536ita/gestionale-libreria/releases/latest):
un file solo per Intel e Apple Silicon. È **firmato ad-hoc** — nessun
certificato Apple, nessuna notarizzazione — perché senza una firma Apple
Silicon rifiuta di eseguire un binario preso dalla rete.

Gatekeeper avvisa comunque, perché la notarizzazione non c'è: **Impostazioni di
sistema → Privacy e sicurezza → Apri comunque**, oppure
`xattr -dr com.apple.quarantine "/Applications/Gestionale Libreria.app"`.

Qui i dati stanno in
`~/Library/Application Support/it.alexkill536ita.gestionale-libreria/`.

### Il servizio della biblioteca

Serve solo se più computer lavorano sullo stesso catalogo; da soli basta l'app.
Sta nella stessa pagina, in file suoi: un installer per Windows, che installa
un servizio di sistema e quindi chiede l'amministratore, un `.pkg` per macOS, un
`.deb` e un `.tar.gz` per Linux (amd64 e arm64), e un `Dockerfile` nella guida.
La guida al primo avvio dell'app lo sa anche installare su questo computer.
Il servizio e l'app devono essere **della stessa versione**.

> [!NOTE]
> Il `.pkg` per macOS non è ancora stato provato su un Mac, e il `.deb` solo in
> un container: se li usi, [dicci com'è andata](#partecipare).

Come si mette in piedi, piattaforma per piattaforma, sta in [Installare il
servizio](wiki/it/Installare-il-servizio.md).

## Documentazione

| | |
|---|---|
| 📘 [**Guida d'uso**](wiki/it/Home.md) | venticinque pagine con le schermate: catalogo, metadati, copertine, serie, editori, prestiti, da acquistare, scanner, storico, dizionari, il catalogo su un server, backup, aggiornamenti — e il servizio della biblioteca: installarlo, utenti, gruppi e permessi, i modi di entrare, lavorare in biblioteca |
| 📗 [**User guide**](wiki/en/Home.md) | the same twenty-five pages, in English — the library service included |

## Partecipare

Il programma e questa documentazione sono MIT; **il codice sta in un repository a
parte**, e non per tenerlo nascosto: perché chi partecipa lo fa **dopo aver
chiesto**, non prima. Leggerlo, correggere un difetto, portarlo dove non arriva,
collaudarlo su un Mac — si dice cosa si ha in mente, e ci si accorda.

[**Chiedere di partecipare**](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=partecipare.yml)
· [*Ask in English*](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=take-part.yml)

Per un difetto quel modulo non serve: ce n'è uno suo —
[**segnalare un difetto**](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=difetto.yml)
· [*in English*](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=bug.yml)
— e per l'idea di una funzione basta una segnalazione libera. In nessuno dei due
casi c'entra il codice.

## Licenza

[MIT](LICENSE) — Copyright © 2026 Alexkill536ITA.

<div align="center">
<br>
<sub>Progetto personale. Nessun account se lo usi da solo, nessuna telemetria, nessun updater —<br>
l'applicazione ti avvisa che una versione è uscita, ma non la scarica e non la installa.</sub>
</div>
