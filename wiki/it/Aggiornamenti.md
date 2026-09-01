**Italiano** · [English](../en/Updates.md)

# Aggiornamenti

All'avvio l'applicazione guarda se è uscita una versione più nuova. Se c'è, lo
dice; se non c'è, non dice niente e non ti accorgi di nulla.

**Non scarica e non installa niente da sé.** L'unica cosa che fa è leggere
l'elenco delle versioni pubblicate e mostrarti cosa cambia: il file da
installare lo scarichi e lo lanci tu, quando vuoi.

![La sezione Aggiornamenti](immagini/impostazioni-aggiornamenti.png)

## L'avviso all'avvio

Quando c'è una versione nuova, all'apertura compare un riquadro che dice **quale
versione è uscita**, **quale hai tu**, quando è stata pubblicata e le **novità**
scritte da chi l'ha pubblicata. Se l'elenco è lungo, scorre.

Tre uscite, e nessuna installa niente:

| | |
|---|---|
| **Aggiorna ora** | apre la pagina della versione nel browser, dove trovi il file `.exe` da scaricare |
| **Più tardi** | chiude e non fa niente: al prossimo avvio te lo ricorda |
| **Salta questa versione** | la mette da parte. Non se ne riparla più, finché non ne esce un'altra |

«Salta questa versione» non è definitivo: quella versione resta scaricabile dalle
Impostazioni, che ti ricordano di averla messa via.

**Premere «Aggiorna ora» non aggiorna niente da solo.** Apre solo la pagina: dopo
aver scaricato il file, l'installazione è quella descritta in
[Installazione](Installazione.md) — si installa sopra, e i dati restano dove
sono.

## Cercare adesso

**Impostazioni → Aggiornamenti**, il quarto scomparto del binario. Qui trovi:

- la **versione installata**, che è quella che sta girando in questo momento;
- **Cerca aggiornamenti**, che chiede subito senza aspettare il prossimo avvio;
- se c'è una versione nuova, il suo numero, la data e le novità, con il pulsante
  **Vai alla pagina della release**.

La riga sotto la voce **Aggiornamenti** nel binario riassume la situazione senza
aprire lo scomparto: `0.1.0 · controllo all'avvio` quando è tutto tranquillo,
`0.1.0 · 0.2.0 disponibile` quando c'è qualcosa da scaricare.

## Spegnere il controllo

La spunta **Cerca aggiornamenti all'avvio** si può togliere. Spenta, l'avviso non
compare più e l'applicazione non contatta nessuno all'avvio: resta il pulsante
**Cerca aggiornamenti**, da premere quando ti va.

Acceso, il controllo costa **una richiesta** all'apertura del programma, e
l'avviso compare **una volta per versione** — non a ogni avvio.

## Cosa viaggia in rete

Una richiesta a GitHub, che chiede l'elenco delle versioni pubblicate di questo
programma. **Non manda niente di tuo**: né i libri, né quanti sono, né un
identificativo. Non c'è un account, non c'è telemetria, e la risposta è la stessa
per chiunque la chieda.

Se sei senza rete, il controllo non riesce e **non te lo dice**: non hai chiesto
niente, e un avviso all'avvio per una cosa che non hai chiesto sarebbe solo
rumore. Premendo **Cerca aggiornamenti**, invece, la risposta te la dà — perché
là l'hai chiesta tu.

## I messaggi che puoi vedere

**«Su GitHub non c'è ancora nessuna versione pubblicata…»** — non è un guasto:
vuol dire che nessuna versione è stata ancora pubblicata pubblicamente, e quella
che hai è l'unica che esiste.

**«Non riesco a raggiungere GitHub…»** — manca la connessione, oppure GitHub è
irraggiungibile da qui. Il catalogo non ne è toccato in alcun modo: riprova più
tardi.

**«GitHub ha risposto con un errore (HTTP …)»** — il problema è dall'altra parte
e passa da sé. Riprova fra qualche minuto.

**«Non riesco ad aprire … nel browser»** — l'indirizzo è nel messaggio: copialo a
mano nella barra degli indirizzi.

## Perché non si aggiorna da sé

Un aggiornamento automatico è un canale attraverso cui, da fuori, arriva del
codice che il tuo computer esegue. Tenerlo in piedi in sicurezza vuol dire
firmare ogni versione con una chiave e pubblicarla insieme al file: lavoro e
attenzione continui, per un programma che installi tu, su un computer solo.

La scelta è stata di fermarsi all'avviso. Così **nessun programma esterno può
farsi installare al posto dell'aggiornamento**, perché non esiste niente che
installi. Quello che entra è il testo di un elenco di versioni; l'unica cosa che
si apre è una pagina del browser.
