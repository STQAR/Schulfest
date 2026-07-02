# Schulfest Pfarrkirchen bei Bad Hall – Tombola-Onepager

Statische One-Pager-Website, die vorab die Hauptpreise der Tombola und die
Sponsoren dahinter zeigt. Der Weblink wird per QR-Code auf Flyern auf den
Tischen ausgehängt. Zielgerät ist primär das **Smartphone** (QR-Scan am Tisch).

## Stack & Aufbau
- **Eine einzige Datei:** `index.html` – kompletter Inhalt, CSS inline, kein Build-Schritt.
- Schriften via Google Fonts: **Baloo 2** (Headlines) + **Nunito** (Fließtext).
- Farbwelt: Grün `#1E6B4E` / Dunkelgrün `#14503A`, Gelb `#FFC93C`, Rot `#E4572E`,
  Papier `#FDFBF5`. Mobile-first, responsive (Media-Query ≤ 480 px).

## Dateien im Repo
- `index.html` – die Seite.
- `volksschule.jpg` – Foto des Schulgebäudes (Foto-Band unter dem Hero).
- `.nojekyll` – schaltet die Jekyll-Verarbeitung ab (leere Datei, nicht löschen).
- `CLAUDE.md` – diese Datei.

## WICHTIGE Konventionen
- **Dateinamen immer klein schreiben, inklusive Endung** (`.jpg`, nicht `.JPG`).
  GitHub Pages ist Groß-/Klein-empfindlich – ein falscher Buchstabe = Bild lädt nicht.
- **Bilder web-optimiert** ablegen (JPEG, ~Qualität 80, progressiv, Metadaten entfernt).
- Preis-Fotos ersetzen die eingebauten SVG-Platzhalter **automatisch**, sobald eine
  Datei mit exakt diesem Namen im Repo liegt:
  `tinyhouse.jpg`, `spar-korb.jpg`, `billa-korb.jpg`.
  Fehlt das Foto, bleibt der Platzhalter stehen (kein kaputtes Bild).

## Inhalte pflegen
- **Hauptpreis:** Abschnitt `#preise` zeigt bewusst NUR den Hauptpreis
  (TinyHouse-Gutschein, romantisches Wochenende für 2) als `<article class="los hauptpreis">`.
  Die Geschenkkörbe (SPAR/BILLA) laufen als Chips unter `#weitere-preise`;
  ihre Fotos (`spar-korb.jpg`/`billa-korb.jpg`) bleiben im Repo für eine spätere
  Wieder-Aufwertung zur Karte (einfach `<article class="los">` duplizieren).
- **Weitere Preise (Auszug):** Abschnitt `#weitere-preise`, zwei `.gewinn-gruppe`-Blöcke
  (Sachpreise / Gutscheine) mit `.chips`-Listen – je Gewinn ein `<span class="chip">`.
- **Sponsoren:** Zwei Ebenen. (1) `.sponsor-grid` = große Karte(n) für Sponsor(en)
  des Hauptpreises (aktuell nur WOLF Haus, solange nur der Hauptpreis beworben wird).
  (2) `.sponsor-wall` = alphabetische Logo-Wand (Kacheln bewusst groß mit viel
  Freiraum: Tile ~220px, Logo bis 88px Höhe, Padding 22×28px), je Sponsor eine
  `.sponsor-tile` (`<img src="<slug>-logo.png|jpg" alt="Name" loading="lazy">`);
  ohne Logo `.sponsor-tile.nur-name` mit Namenstext (aktuell nur noch
  „Biohof Langwies“ – Logo bewusst nicht eingebaut, siehe unten). Quell-Logos
  normalisiert auf max. 360×160 px vor dem Rendern, Rohdaten in
  `files/Logos_Sponsoren` (tlw. nur im `Sponsorenplakat.pptx` als WMF eingebettet;
  vor dem Verwerfen dort per Contact-Sheet auf neue/fehlende Sponsoren prüfen –
  so wurde z. B. „Der Ruzicka“ nachträglich gefunden, `ruzicka.png` lag unbenutzt
  im Ordner).
- **Eckdaten** (Datum, Ort, Lospreis): Hero-Chips `.fakten` und Footer.
  Aktueller Stand: Fr, 03.07.2026 · Pfarrhof Pfarrkirchen · Los € 3,–.

## Deployment
- **GitHub Pages**, Quelle: Branch `main`, Ordner `/ (root)`.
- **Bekanntes Problem:** GitHubs Pages-Auslieferung kann hängen
  (`deployment_queued` → Timeout). Kein Code-Fehler – serverseitig bei GitHub.
  Dann: Actions → fehlgeschlagenen Lauf → **„Re-run all jobs"** (kein neuer Commit),
  ein paar Minuten warten. Nicht mehrfach kurz hintereinander pushen (Kollisionen).
- **Fallback-Host:** Netlify Drop (`app.netlify.com/drop`) – dieselben Dateien als
  ZIP reinziehen, sofort live, ohne Build-Warteschlange.
