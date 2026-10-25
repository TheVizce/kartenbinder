# Kartenbinder

Meine Pokémon-Kartensammlung – das echte Sammelkartenspiel (TCG) und TCG Pocket – als Web-App auf GitHub Pages.

## Einrichten (einmalig, ca. 5 Minuten)

1. Auf GitHub ein neues Repository anlegen, z. B. `kartenbinder` (öffentlich, sonst braucht GitHub Pages ein Bezahl-Abo).
2. `index.html`, `sammlung.json` und diese `README.md` hochladen (**Add file → Upload files**).
3. **Settings → Pages**: unter *Branch* `main` und `/ (root)` wählen, speichern.
4. Nach ca. einer Minute ist das Tool erreichbar unter `https://<dein-name>.github.io/kartenbinder/`.

## Wo wird meine Sammlung gespeichert?

- **Automatisch im Browser** – jede Änderung wird sofort lokal gesichert.
- **Dauerhaft im Repo** als `sammlung.json`. Zwei Wege dorthin:
  - **Einfach:** ⚙︎ → *Sammlung exportieren* und die Datei im Repo ersetzen.
  - **Komfortabel (empfohlen fürs Handy):** ⚙︎ → *Direkt auf GitHub speichern*. Dafür einmal einen Token erstellen: GitHub → *Settings → Developer settings → Personal access tokens → Fine-grained tokens* → *Only select repositories* → dein Kartenbinder-Repo → *Repository permissions → Contents: Read and write*. Token im Tool eintragen. Ab dann wird jede Änderung nach ein paar Sekunden automatisch committet, und jedes Gerät lädt beim Öffnen den neuesten Stand.

Der Token wird nur im jeweiligen Browser gespeichert, nie im Repo.

## Funktionen

**Sammelkarten (TCG)**
- Alle Serien und Sets (deutsch oder englisch) mit Kartenbildern, Fortschritt pro Set
- Pro Karte: Anzahl je Variante (Normal, Reverse Holo, Holo, 1. Edition), Sprache, Zustand, Notiz
- Cardmarket-Preise (Trend, Ø 30 Tage) und geschätzter Gesamtwert
- Schnellerfassung: Karten im Set einfach antippen

**TCG Pocket**
- Alle Sets inkl. Promos, Fortschritt gesamt, pro Set und pro Seltenheit (◆ ★ ✦ ♛)
- Pro Karte: aus welchem Pack sie kommt und mit welcher Wahrscheinlichkeit pro Pack, Pack-Punkte-Kosten, Tauschkosten
- Pro Pack: Chance auf mindestens eine neue Karte, Ø neue Karten pro Pack, Pack-Punkte für den Rest
- **Pack-Berater:** Rangliste, welches Pack du als Nächstes öffnen solltest
- Schnellerfassung ist hier standardmäßig an: Antippen = habe ich / habe ich nicht. Doppelte über die Kartenansicht zählen.

## Datenquellen

- [TCGdex](https://tcgdex.dev) – Karten, Bilder, Preise (Cardmarket)
- [pokemon-tcg-pocket-database](https://github.com/flibustier/pokemon-tcg-pocket-database) – Pocket-Packs, Zieh-Raten, Pack-Punkte

Neue Sets erscheinen automatisch, sobald die Datenquellen aktualisiert sind – am Tool muss nichts geändert werden.

Inoffizielles Fan-Projekt. Pokémon © Nintendo / Creatures / GAME FREAK.
