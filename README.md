# Cronache dell'Avventuriero: guida al deploy

Web app medieval fantasy collegata a un foglio Google. Contiene:

- **Bacheca delle Missioni**: le attività non programmate (viaggi, gite, esperienze...) da compiere.
- **Mappa del Regno**: i luoghi che segni compaiono come spille (rosse = da compiere, verdi = compiute).
- **Il Tomo delle Gesta**: un diario a pagine. Ogni missione compiuta ottiene una pagina con lo stesso modello: data, titolo, luogo, valutazione, cronaca e foto.
- **Intro a cancelli** in stile videogioco, con braci, titolo animato e portone che si apre.
- **Rango dell'avventuriero** che sale con le missioni compiute.

## File

| File | Dove va |
|---|---|
| `Code.gs` | Nel file `Codice.gs` / `Code.gs` del progetto Apps Script |
| `Index.html` | In un file HTML chiamato esattamente **Index** nel progetto Apps Script |

## Installazione (5 minuti)

1. **Crea un foglio Google** nuovo (o usa uno esistente) e dagli un nome, per esempio "Cronache".
2. Dal foglio vai su **Estensioni → Apps Script**. Si apre l'editor di uno script legato al foglio.
3. Nel file `Codice.gs` cancella tutto e incolla il contenuto di **Code.gs**.
4. Clicca **＋** accanto a "File" → **HTML**, chiamalo `Index` (senza `.html`) e incolla il contenuto di **Index.html**.
5. Salva (Ctrl+S). Dal menu a tendina delle funzioni scegli **`inizializza`** e premi **Esegui**.
   - Google chiede le autorizzazioni (Fogli e Drive): **Avanzate → Vai a ... (non sicuro) → Consenti**. È normale per i tuoi script personali.
   - Vengono creati il foglio **Missioni** e la cartella Drive **Cronache - Foto Avventure**.
6. Clicca **Distribuisci → Nuova distribuzione**:
   - Tipo: **App web** (icona ingranaggio)
   - Descrizione: `Cronache v1`
   - Esegui come: **Me**
   - Chi ha accesso: **Solo io** (consigliato, è il tuo diario privato)
7. Clicca **Distribuisci** e copia l'**URL dell'app web**. È il tuo regno. Aprilo e salvalo tra i preferiti.

### Aggiungerla alla schermata Home del telefono
- **iPhone**: apri l'URL in Safari → Condividi → *Aggiungi a Home*.
- **Android**: apri l'URL in Chrome → ⋮ → *Aggiungi a schermata Home*.

## Aggiornare il sito dopo una modifica al codice

Ogni volta che cambi `Code.gs` o `Index.html`: **Distribuisci → Gestisci distribuzioni → ✏️ Modifica → Versione: Nuova versione → Distribuisci**. L'URL resta lo stesso.

## Come funziona

- **Nuova missione**: pulsante ＋ (anche sul telefono). Scegli titolo, genere, rango, luogo e appunti.
- **Luogo**: scrivi il nome e premi *Cerca* per fissare le coordinate (OpenStreetMap). In alternativa vai su *Mappa del Regno* → *Segna un luogo sulla mappa* e tocca il punto: si apre già la missione con luogo e coordinate.
- **Compiuta!**: si apre la pagina del diario da scrivere, con data, valutazione a stelle, cronaca e foto (da galleria o fotocamera). Le foto vengono ridimensionate automaticamente e salvate in Drive.
- **Il Tomo**: sfogli le pagine con i pulsanti o con le frecce della tastiera. Clic su una foto per ingrandirla.

## Il foglio Google

Il foglio **Missioni** contiene una riga per missione, quindi puoi anche filtrarlo, farne statistiche o grafici:

`id · titolo · categoria · stato · luogo · lat · lng · priorita · dataPrevista · note · dataCompletata · diario · foto · valutazione · creatoIl · aggiornatoIl`

Non cambiare l'ordine e i nomi delle intestazioni nella riga 1. Puoi modificare le celle a mano e l'app le leggerà al prossimo caricamento.

## Note utili

- **Foto**: restano nella cartella Drive *Cronache - Foto Avventure* e vengono condivise con "chiunque abbia il link" in sola visualizzazione, solo per poterle mostrare nel diario. Il link non è indovinabile. Se il tuo account Workspace blocca questa condivisione, le foto potrebbero non apparire: in quel caso chiedi all'amministratore o usa un account Google personale.
- **Accesso "Solo io"**: devi essere loggato con l'account Google che ha fatto il deploy. Se sul telefono la pagina resta bianca, apri l'URL in Chrome/Safari (non in app interne) e accedi.
- **Mappa e ricerca luoghi**: usano OpenStreetMap e Nominatim, gratuiti e senza chiavi API. Va bene per l'uso personale.
- **Script non legato al foglio**: se hai creato lo script da script.google.com, scrivi l'ID del foglio nella costante `SPREADSHEET_ID` in cima a `Code.gs`.
- **Anteprima senza Google**: aprendo `Index.html` direttamente nel browser parte in *modalità demo* con tre missioni d'esempio, salvate solo nel browser. Serve a vedere il design.
- **Personalizzare**: generi e ranghi sono in cima allo script di `Index.html` (`CATS`, `PRIO`, `RANKS`). I colori sono nelle variabili `:root`.
