BACKUP PROGETTO "Lettore TTS Neural & ePub"
Generato il: 2026-08-09

=== COSA CONTIENE QUESTO BACKUP ===

index.html              -> l'app (va caricato su GitHub Pages, repo "reader-app",
                            deve chiamarsi index.html)
manifest.json            -> manifest PWA (stessa cartella di index.html)
icon-*.png                -> icone dell'app (stessa cartella di index.html)
azure-tts-worker.js       -> codice del Cloudflare Worker "azure-tts-proxy"
google-tts-worker.js      -> codice del Cloudflare Worker "google-tts-proxy"
assetlinks.json           -> va caricato su un repository DIVERSO, quello
                            "micmax1000-afk.github.io" (root del dominio),
                            dentro la cartella .well-known/

=== DOVE CARICARE COSA ===

Repository "reader-app" (GitHub Pages):
  - index.html
  - manifest.json
  - icon-16.png, icon-32.png, icon-180.png, icon-192.png,
    icon-512.png, icon-maskable-512.png

Repository "micmax1000-afk.github.io" (root del dominio):
  - .well-known/assetlinks.json

Cloudflare Workers (incollare nell'editor codice di ciascun Worker):
  - Worker "azure-tts-proxy"  <- azure-tts-worker.js
  - Worker "google-tts-proxy" <- google-tts-worker.js

=== VARIABILI/SECRET DA IMPOSTARE SUI WORKER ===
(da re-inserire manualmente, Cloudflare non permette di esportarle)

Worker azure-tts-proxy:
  - AZURE_SPEECH_KEY    (Secret)
  - AZURE_SPEECH_REGION = italynorth
  - APP_SECRET          (Secret) = deve combaciare con APP_TOKEN dentro index.html

Worker google-tts-proxy:
  - GOOGLE_TTS_API_KEY  (Secret)
  - APP_SECRET          (Secret) = stesso valore di sopra

Il token APP_TOKEN è già scritto dentro index.html (variabile APP_TOKEN in cima
allo script) - se lo perdi, aprilo e cercalo lì.

=== CHIAVE DI FIRMA ANDROID (APK) ===
NON inclusa in questo backup per motivi di sicurezza - il file signing.keystore
e le sue credenziali (password: FFuLgMrQWVqu, alias: my-key-alias) li hai
ricevuti separatamente da PWABuilder quando hai generato il pacchetto.
CONSERVALI TU IN UN POSTO SICURO: senza quel file non puoi più aggiornare
la stessa identica app Android in futuro (dovresti reinstallarla da zero
con una firma diversa, perdendo il collegamento con assetlinks.json attuale).

=== URL DEL PROGETTO ===
App:              https://micmax1000-afk.github.io/reader-app/
Worker Azure:      https://azure-tts-proxy.mic-max-1000.workers.dev
Worker Google:     https://google-tts-proxy.mic-max-1000.workers.dev
Package Android:   readertts.micmax1000_afk.twa
