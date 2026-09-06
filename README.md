# Asta Fanta — app con sincronizzazione in tempo reale

App per gestire l'asta del fantacalcio con analisi giocatori, banditore live e
sincronizzazione in tempo reale tra più dispositivi (via Supabase).

## Cosa contiene

```
asta-fanta-app/
├── index.html          punto di ingresso
├── package.json        dipendenze e comandi
├── vite.config.js      configurazione build
├── vercel.json         routing per Vercel
├── src/
│   ├── main.jsx        avvia l'app React
│   └── App.jsx         tutta l'applicazione
```

Il database Supabase è già configurato dentro `src/App.jsx` (URL + chiave).
La tabella `asta_stato` è già stata creata sul progetto Supabase.

---

## Provarla sul tuo computer (facoltativo)

Serve Node.js installato (https://nodejs.org).

```bash
cd asta-fanta-app
npm install
npm run dev
```

Apri l'indirizzo che compare (di solito http://localhost:5173).

---

## Pubblicarla online su Vercel (gratis)

### Modo A — via GitHub (consigliato, aggiornamenti automatici)

1. Crea un repository su https://github.com e carica dentro **tutta** la
   cartella `asta-fanta-app` (senza `node_modules`).
2. Vai su https://vercel.com e accedi con GitHub.
3. **Add New… → Project**, scegli il repository.
4. Vercel riconosce Vite da solo. Lascia i valori di default:
   - Framework Preset: **Vite**
   - Build Command: `npm run build`
   - Output Directory: `dist`
5. Premi **Deploy**. Dopo ~1 minuto avrai un link pubblico (es.
   `asta-fanta.vercel.app`) da condividere con Admin e Developer.

### Modo B — senza GitHub (drag & drop)

1. Sul tuo computer esegui `npm install` poi `npm run build`: crea la cartella `dist`.
2. Vai su https://vercel.com → **Add New… → Project → Deploy** e trascina la
   cartella `dist`. (Con questo metodo, per aggiornare l'app dovrai ripetere il
   build e ricaricare `dist`.)

---

## Come si usa

- Chi apre il link vede la schermata di accesso: **Admin lega** (entra subito)
  oppure **Developer** (password richiesta).
- Tutti vedono lo stesso stato dell'asta in tempo reale (pallino verde "live"
  in alto). Quando qualcuno aggiudica un giocatore, gli altri lo vedono in 1-2 secondi.
- Consiglio pratico: durante l'asta, **una sola persona conduce** (usa il
  banditore e aggiudica); gli altri guardano. Così non ci sono conflitti di modifica.

## Note

- La password del Developer è nel codice (`src/App.jsx`, costante `DEV_PASSWORD`).
  Per cambiarla, modifica quella riga e ripubblica.
- Se il pallino in alto è rosso ("offline"), controlla la connessione internet o
  che la tabella `asta_stato` esista ancora su Supabase.
