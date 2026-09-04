**Italiano** · [English](../en/Installation.md)

# Installazione

L'applicazione gira su **Windows 10 e 11**, e da settembre 2026 anche su
**macOS**: ogni versione porta un file suo, e come si installa lo dice
[Su un Mac](#su-un-mac).

Su Windows non serve altro: il componente di sistema che disegna la finestra
(WebView2) è dentro l'installatore, quindi non viene scaricato durante
l'installazione.

## Installare su Windows

1. Scarica il file `Gestionale Libreria_0.4.0_x64-setup.exe`.
2. Doppio clic. L'installatore parla italiano e chiede poco.
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

Il file è `Gestionale Libreria_0.4.0_universal.dmg`, uno solo per i Mac Intel e
per quelli con Apple Silicon: si apre, si trascina l'applicazione in
**Applicazioni**, e da lì si avvia.

> [!NOTE]
> Se qualcosa non va, è un
> [difetto da segnalare](https://github.com/alexkill536ita/gestionale-libreria/issues/new?template=difetto.yml)
> — non un tuo errore.

Al primo avvio macOS dice che l'applicazione **non può essere verificata**, per lo
stesso motivo per cui Windows mostra SmartScreen: non c'è un certificato pagato ad
Apple. Si passa da **Impostazioni di sistema → Privacy e sicurezza**, dove compare
il pulsante **Apri comunque**.

I tuoi dati stanno qui, e vale tutto quello che dice il resto di questa pagina:

```
~/Library/Application Support/it.alexkill536ita.gestionale-libreria/
```

## Dove finiscono i dati

Su Windows tutto quello che è tuo sta in una cartella sola:

```
%LOCALAPPDATA%\it.alexkill536ita.gestionale-libreria\
```

Incolla quel percorso nella barra di Esplora risorse e ci arrivi. Dentro trovi:

| | |
|---|---|
| `libreria.db` | il catalogo — è questo il file che conta |
| `covers\` | le copertine, un JPEG per libro |
| `backups\` | le copie automatiche, se non ne hai scelta un'altra |
| `impostazioni.json` | tema, lingua, valuta, chiave API, cartella dei backup |

Il **programma** invece sta altrove, in `%LOCALAPPDATA%\Gestionale Libreria\` —
non in `Programmi`, dove di solito lo si cerca.

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
