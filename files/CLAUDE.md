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
- **Top-Preise:** Abschnitt `#preise`, je Preis ein `<article class="los">`
  (Hauptpreis zusätzlich Klasse `hauptpreis`). Für weitere Preise Karte duplizieren.
- **Sponsoren:** Abschnitt `.sponsor-grid`, je Sponsor eine `.sponsor-karte`
  (mit Logo `<img>` oder nur Name). Zentriertes Flex-Layout, beliebig viele Karten.
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
