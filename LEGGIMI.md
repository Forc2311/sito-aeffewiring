# Sito Web A Effe Wiring and Service — Istruzioni

Il sito è **un solo file** (`index.html`), niente da installare, gratis per
sempre su GitHub Pages con il tuo dominio `aeffewiring.com`.

---

## 1. Crea un account GitHub (se non ce l'hai già)

Vai su https://github.com/signup e registrati (gratis).

## 2. Crea un nuovo repository

1. Una volta loggato, clicca il **+** in alto a destra → **New repository**
2. Nome: scrivi ad esempio `sito-aeffewiring` (il nome non compare nell'indirizzo finale, quindi va bene qualsiasi nome)
3. Assicurati che sia impostato su **Public** (obbligatorio per GitHub Pages gratuito)
4. Clicca **Create repository**

## 3. Carica i file (senza bisogno di comandi/git)

1. Nella pagina del repository appena creato, clicca **"uploading an existing file"** (o **Add file → Upload files**)
2. Trascina dentro **tutti i file** di questa cartella: `index.html`, `privacy.html`, `cookie.html`, `policies.html`, `404.html`, `CNAME`, `logo.jpg`, `favicon.svg`, `favicon.ico`, `apple-touch-icon.png`, `og-image.png`, `robots.txt` e `sitemap.xml`
3. Scorri in basso, clicca **Commit changes**

## 4. Attiva GitHub Pages

1. Nel repository, vai su **Settings** (in alto)
2. Nel menu a sinistra, clicca **Pages**
3. Sotto "Build and deployment" → **Source**, scegli **Deploy from a branch**
4. Branch: **main**, cartella: **/ (root)** → **Save**
5. Sotto "Custom domain", dovrebbe già comparire `aeffewiring.com` (letto dal
   file CNAME che hai caricato) — se non c'è, scrivilo tu e premi **Save**

A questo punto GitHub ti mostra un avviso che il DNS non è ancora configurato — è normale, lo sistemiamo subito.

## 5. Configura il DNS su Squarespace Domains

1. Vai su https://domains.squarespace.com e fai login
2. Apri il dominio `aeffewiring.com` → **DNS Settings** (o "Impostazioni DNS")
3. Aggiungi **4 record di tipo A**, tutti con host/nome vuoto (o `@`), che puntano a:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
   (uno per record — quattro righe separate)
4. Aggiungi anche un record **CNAME**:
   - Host/nome: `www`
   - Valore: `IL-TUO-USERNAME-GITHUB.github.io` (sostituisci con il tuo username GitHub, es. se il tuo profilo è `github.com/andreaforcellini`, scrivi `andreaforcellini.github.io`)
5. Se vedi già record A o CNAME preesistenti che puntano altrove (es. verso Squarespace stesso), **rimuovili prima** di aggiungere questi nuovi, altrimenti vanno in conflitto

## 6. Aspetta la propagazione e attiva HTTPS

1. Il DNS può metterci da pochi minuti a 24 ore per propagarsi
2. Torna su GitHub → Settings → Pages: quando il pallino diventa verde, il dominio è riconosciuto
3. Spunta **"Enforce HTTPS"** (potrebbe comparire disponibile solo dopo la propagazione — se non c'è subito, ricontrolla il giorno dopo)

Da questo momento, `https://aeffewiring.com` mostra il tuo sito.

---

## Come aggiungere le foto dei lavori (quando le hai)

Nella sezione "Progetti" del sito ci sono 3 caselle tratteggiate con scritto
"Foto in arrivo" — sono segnaposto pronti da sostituire.

1. Apri `index.html` (puoi modificarlo direttamente su GitHub: apri il file
   nel repository, clicca l'icona della matita ✏️ in alto a destra)
2. Cerca (Ctrl+F nel browser) il testo `Foto in arrivo`
3. Per ogni casella, sostituisci questo blocco:
   ```html
   <div class="prog-card">
     <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4"><rect x="3" y="4" width="18" height="16" rx="1"/><path d="M3 9h18M8 4v5M8 13h8M8 17h5"/></svg>
     <div class="txt">Foto in arrivo</div>
   </div>
   ```
   con:
   ```html
   <div class="prog-card" style="border-style:solid; padding:0; overflow:hidden;">
     <img src="progetti/nome-foto.jpg" alt="Descrizione del lavoro" style="width:100%; height:100%; object-fit:cover;">
   </div>
   ```
4. Carica le foto vere in una cartella `progetti/` dentro il repository
   (crea la cartella caricando i file con quel percorso, oppure usa
   "Add file → Upload files" e trascina le immagini lì dentro)
5. **Commit changes** — il sito si aggiorna da solo in un minuto o due

Se vuoi aggiungere più di 3 progetti, copia e incolla un blocco `prog-card`
in più per ognuno — la griglia si adatta da sola.

## Modificare i testi

Tutti i testi (Chi siamo, Servizi, Contatti) sono dentro `index.html`, in
italiano semplice, facili da trovare e modificare direttamente dall'editor
di GitHub (icona matita) — non serve altro software.

## Se qualcosa non funziona

- **Il sito non si apre**: aspetta più tempo per la propagazione DNS (fino a
  24 ore), poi ricontrolla i record A e CNAME su Squarespace
- **Errore "Domain's DNS record could not be retrieved"** su GitHub: di
  solito sparisce da solo entro un'ora dalla configurazione DNS
- **HTTPS non si attiva**: aspetta che il dominio risulti verificato
  (pallino verde) prima di spuntare "Enforce HTTPS"

Se ti blocchi in qualche passaggio, mandami uno screenshot di dove sei
arrivato e ti aiuto a sbloccarlo.

## Come farsi trovare su Google (gratis)

Il sito da solo non basta — Google deve "scoprirlo". Tre cose gratuite da fare:

1. **Google Business Profile** (business.google.com) — crea la scheda della tua
   azienda con nome, indirizzo, sito. È la cosa più efficace per farti trovare
   quando qualcuno cerca proprio "A Effe" — compare quasi subito, prima ancora
   che il sito si posizioni bene nei risultati normali.
2. **Google Search Console** (search.google.com/search-console) — aggiungi il
   sito, verificalo, poi usa "Controllo URL" → "Richiedi indicizzazione" sulla
   homepage. Così dici esplicitamente a Google di venire a leggere il sito
   subito, invece di aspettare che lo trovi da solo (può volerci settimane).
3. Il sito include già `sitemap.xml` e `robots.txt` (li trovi in questa
   cartella, vanno caricati insieme agli altri file) — aiutano Google a
   capire la struttura del sito una volta che lo visita.

Aspettati qualche giorno prima di vedere risultati, anche facendo tutto bene
— è normale, non è un problema del sito.
