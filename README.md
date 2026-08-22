# Repository — I Miei Progetti

App single-page protetta da password per raccogliere, organizzate in sezioni, tutte le tue app interattive pubblicate su GitHub Pages.

**Login e contenuti sono condivisi tra tutti i browser e dispositivi**: non vengono salvati solo nel browser locale, ma letti e scritti in un file `data.json` dentro il tuo stesso repository GitHub. Così, ovunque apri la pagina, vedi le stesse credenziali e le stesse sezioni/link.

## Primo utilizzo

Alla primissima apertura, l'app cerca il file dati sul repository e non lo trova: compare quindi una schermata di configurazione in cui:

1. scegli utente e password che vuoi usare per accedere;
2. incolli un **token GitHub** con permesso di scrittura, necessario solo in questo momento per creare il file.

Da quel momento, il file `repository-hub/data.json` esiste sul repository e contiene utente, password (in forma cifrata, non in chiaro) e tutte le sezioni/link.

### Come creare il token GitHub

1. Vai su [github.com/settings/personal-access-tokens/new](https://github.com/settings/personal-access-tokens/new) (token "fine-grained").
2. Seleziona il tuo account come "Resource owner" e limita l'accesso al repository interessato (es. `Repository`).
3. In "Repository permissions" imposta **Contents: Read and write**.
4. Genera il token e incollalo nell'app quando richiesto.

Il token resta salvato **solo nel browser in cui lo incolli** (mai nel file su GitHub). Serve per poter **modificare** sezioni e link da quel dispositivo; se apri l'app da un browser nuovo senza incollare il token, puoi comunque **accedere e vedere** tutto il contenuto, ma per modificarlo l'app ti chiederà di aggiungere un token da "Impostazioni GitHub".

## Accesso da un altro browser o dispositivo

Basta aprire la pagina e inserire le stesse credenziali: vengono verificate leggendo il file dal repository, quindi funzionano ovunque. Se vuoi anche modificare sezioni/link da quel dispositivo, apri "Impostazioni GitHub" e incolla un token con permesso di scrittura (puoi usare lo stesso token su più dispositivi, oppure crearne uno diverso per ciascuno).

## Funzioni

- **Sezioni**: crea con "+ Nuova sezione", cancella con la ✕ sulla card.
- **Link**: dentro ogni sezione, aggiungi nome + URL della tua app (es. `https://gianlucaronzio.github.io/Repository/...`), cancella con la ✕ accanto al link.
- **Cambia credenziali**: dal menu in alto, aggiorna utente/password — viene salvato subito sul repository, valido ovunque dal prossimo accesso.
- **Aggiorna dati**: ricarica manualmente l'ultima versione dal repository (utile se hai fatto modifiche da un altro dispositivo).
- **Esporta/Importa backup**: scarica o carica un file `.json` locale con le sole sezioni, come backup aggiuntivo.
- **Impostazioni GitHub**: cambia proprietario/repository/percorso file/branch, o aggiorna il token su quel browser.

## Deploy su GitHub Pages

1. Carica `index.html`, `README.md` e `_config.yml` nel repository `gianlucaronzio/Repository` (es. in una sottocartella `hub/`).
2. Attiva GitHub Pages sul repository, se non già attivo.
3. Visita l'URL pubblicato: alla prima apertura ti verrà chiesto di configurare utente, password e token (vedi sopra).

## Note sulla sicurezza

- La password non è salvata in chiaro nel file su GitHub: viene salvata come impronta SHA-256. Resta comunque una protezione client-side, adatta a scoraggiare visitatori occasionali di un repository pubblico, non a proteggere dati realmente sensibili.
- Il file `data.json`, se il repository è pubblico, è leggibile da chiunque conosca l'URL diretto (contiene sezioni, link e l'impronta della password, non la password in chiaro).
- Il token GitHub va trattato come una password: non condividerlo, e puoi revocarlo in qualsiasi momento da github.com/settings/tokens.
- Se più persone modificano contemporaneamente da dispositivi diversi, vince l'ultimo salvataggio; in caso di conflitto l'app ricarica automaticamente i dati più recenti e ti chiede di ripetere la modifica.
