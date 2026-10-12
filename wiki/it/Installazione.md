**Italiano** · [English](../en/Installation.md)

# Installazione

L'applicazione gira su **Windows 10 e 11**, e da settembre 2026 anche su
**macOS**: ogni versione porta un file suo, e come si installa lo dice
[Su un Mac](#su-un-mac).

Questa pagina parla dell'app. Il **servizio della biblioteca** — il programma
che tiene un catalogo solo per più computer, ognuno con il suo accesso — si
installa a parte, e lo racconta [Installare il servizio](Installare-il-servizio.md).

Su Windows non serve altro: il componente di sistema che disegna la finestra
(WebView2) è dentro l'installatore, quindi non viene scaricato durante
l'installazione.

## Installare su Windows

1. Scarica il file `Gestionale Libreria_0.7.5_x64-setup.exe`.
2. Doppio clic. L'installatore chiede per prima cosa la lingua, italiano o
   inglese, e propone quella di Windows; poi chiede poco.
3. Finito: trovi il collegamento **sul desktop** e **nel menu Start**.

L'installazione è **per il solo utente corrente**: non chiede i permessi di
amministratore e non tocca il resto del computer.

## «Windows ha protetto il PC»

Al primo avvio dell'installatore Windows mostra una schermata blu di SmartScreen
con quel titolo. Succede perché **il programma non ha una firma digitale**, e non
è un segnale che il file sia stato manomesso: un certificato costa un canone
annuo e, da solo, non spegnerebbe nemmeno l'avviso.

Per proseguire: **Ulteriori informazioni** → **Esegui comunque**.

## Su un Mac

Il file è `Gestionale Libreria_0.7.5_universal.dmg`, uno solo per i Mac Intel e
per quelli con Apple Silicon: si apre, si trascina l'applicazione in
**Applicazioni**, e da lì si avvia. È stato provato su un Mac, e funziona.

Al primo avvio macOS dice che l'applicazione **non può essere verificata**, per lo
stesso motivo per cui Windows mostra SmartScreen: non c'è un certificato pagato ad
Apple. Si passa da **Impostazioni di sistema → Privacy e sicurezza**, dove compare
il pulsante **Apri comunque**. Se preferisci il Terminale, la stessa cosa si fa
con:

```
xattr -dr com.apple.quarantine "/Applications/Gestionale Libreria.app"
```

La prima volta che apri la [scansione del codice a
barre](Scansionare-il-codice-a-barre.md), **macOS chiede il permesso di usare la
fotocamera**: concedilo, o il mirino resta nero. Se l'hai negato, si riaccende da
**Impostazioni di sistema → Privacy e sicurezza → Fotocamera**.

Per **aggiornare** si trascina l'applicazione nuova in **Applicazioni** e si
sceglie di sostituire quella che c'è; per **disinstallare** la si trascina nel
Cestino. In tutti e due i casi la cartella dei dati resta dov'è.

I tuoi dati stanno qui, e vale tutto quello che dice il resto di questa pagina:

```
~/Library/Application Support/it.alexkill536ita.gestionale-libreria/
```

## Dove finiscono i dati

Su Windows, di partenza, tutto quello che è tuo sta in una cartella sola:

```
%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\
```

Incolla quel percorso nella barra di Esplora risorse e ci arrivi. Dentro trovi:

| | |
|---|---|
| `libreria.db` | il catalogo — è questo il file che conta |
| `covers\` | le copertine, un JPEG per libro |
| `miniature\` e `intermedie\` | copie ridotte delle copertine, per le viste piccole e per quelle grandi: si rifanno da sole dall'originale, e cancellarle non perde niente |
| `backups\` | i backup che chiedi tu, se non ne hai scelta un'altra |
| `impostazioni.json` | tema, lingua, valuta, chiave API, fotocamera, cartella dei backup e del catalogo, la versione che hai saltato, e il collegamento al server — **password compresa**, come le chiavi dell'archivio S3 |

Il catalogo — `libreria.db` e `covers\`, con i suoi `backups\` se non ne hai
scelta un'altra — **si può spostare** in un'altra cartella, o stare **su un
server**: lo raccontano [Dove stanno i dati](Dove-stanno-i-dati.md) e
[Il catalogo su un server](Il-catalogo-su-un-server.md). `impostazioni.json`,
`miniature\` e `intermedie\` restano invece sempre qui, perché sono di questo
computer.

Il **programma** invece sta altrove, in `%LOCALAPPDATA%\Gestionale Libreria\` —
non in `Programmi`, dove di solito lo si cerca. Accanto all'eseguibile c'è
`AVVISI-LICENZE.txt`, che raccoglie le licenze dei mille e passa componenti di
altri che il programma incorpora. Non serve andarlo a cercare: lo apre il
programma, dall'ingranaggio in alto a destra, voce **Licenza** — dove c'è anche
la licenza di Gestionale Libreria. Lo stesso elenco sta in [Licenze dei
componenti](Licenze-dei-componenti.md).

## Aggiornare

**L'applicazione ti avvisa quando esce una versione nuova**, ma non la scarica e
non la installa: apre la pagina da cui prendere il file, e il resto lo decidi tu.
Il giro per esteso è in [Aggiornamenti](Aggiornamenti.md).

Per passare a una versione nuova si **installa sopra**, come la prima volta:
**i dati restano dove sono** e li ritrovi tutti. Non serve disinstallare prima.

## Disinstallare

Da **Impostazioni di Windows → App**, oppure con `uninstall.exe` nella cartella
del programma.

**La disinstallazione non cancella il catalogo.** Spariscono il programma, i due
collegamenti e la voce nell'elenco delle app; la cartella dei dati resta al suo
posto, e reinstallando ritrovi tutto. Se vuoi davvero ripartire da zero, quella
cartella va svuotata a mano — ma prima [fai un backup](Backup-e-ripristino.md) e
mettilo altrove.
