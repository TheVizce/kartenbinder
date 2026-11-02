# Kartenbinder

Meine Pokémon-Kartensammlung – das echte Sammelkartenspiel (TCG) und TCG Pocket – als Web-App auf GitHub Pages.

## Einrichten (einmalig, ca. 5 Minuten)

1. Auf GitHub ein neues Repository anlegen, z. B. `kartenbinder` (öffentlich, sonst braucht GitHub Pages ein Bezahl-Abo).
2. `index.html` und diese `README.md` hochladen (**Add file → Upload files**).
3. **Settings → Pages**: unter *Branch* `main` und `/ (root)` wählen, speichern.
4. Nach ca. einer Minute ist das Tool erreichbar unter `https://<dein-name>.github.io/kartenbinder/`.

## Wo wird meine Sammlung gespeichert?

- **Automatisch im Browser** – jede Änderung wird sofort lokal gesichert, in der IndexedDB-Datenbank `kartenbinder` (Sammlung, Zwischenspeicher für Kartendaten). Im localStorage liegt nur `kartenbinder.settings` (Ansicht und Filter, wenige hundert Byte).
- Schlägt das Speichern fehl (z. B. Speicher voll), erscheint oben ein roter Hinweis mit „Exportieren“ und „Erneut speichern“. Solange er sichtbar ist, warnt der Browser auch beim Schließen der Seite.
- **Auf allen Geräten** über den gemeinsamen GitHub-Sync der Tools (`/startseite/sync-v1.js`): privates Repo `tool-daten`, Ordner `kartenbinder/` (main.json + 16 Teildateien). Repo und Token werden einmal pro Gerät auf der Startseite eingetragen. Pro Karte gewinnt die jüngste Änderung; beim ersten Abgleich eines Geräts wird der vorhandene Cloud-Stand übernommen (der lokale Stand landet vorher in einer Sicherheitskopie, Startseite → GitHub-Sync).
- Zusätzlich: ⚙︎ → *Sammlung exportieren* als JSON-Sicherung.

Bis 02.11.2026 lag die Sammlung als `sammlung.json` in diesem öffentlichen Repo; sie wird nicht mehr geschrieben oder gelesen.

## Funktionen

**Sammelkarten (TCG)**
- Alle Serien und Sets (deutsch oder englisch) mit Kartenbildern, Fortschritt pro Set
- Pro Karte: Anzahl je Variante (Normal, Reverse Holo, Holo, 1. Edition), Sprache, Zustand, Notiz
- Cardmarket-Preise (Trend, Ø 30 Tage) und geschätzter Gesamtwert
- Schnellerfassung: Karten im Set einfach antippen
- Filter (Habe ich, Fehlen, Doppelte, ★ Wunsch) und Sortierung; Sammlung sortierbar nach Set, Datum, Name oder Wert
- **Binder-Ansicht:** Set als Ordnerseiten mit 4, 9 oder 12 Taschen
- **Wunschliste** mit Suchliste zum Kopieren (praktisch für Tauschbörsen)

**TCG Pocket**
- Alle Sets inkl. Promos, Fortschritt gesamt, pro Set und pro Seltenheit (◆ ★ ✦ ♛)
- Pro Karte: aus welchem Pack sie kommt und mit welcher Wahrscheinlichkeit pro Pack, Pack-Punkte-Kosten, Tauschkosten
- Pro Pack: Chance auf mindestens eine neue Karte, Ø neue Karten pro Pack, Pack-Punkte für den Rest
- **Pack-Berater:** Rangliste, welches Pack du als Nächstes öffnen solltest
- Schnellerfassung: Antippen setzt eine Karte auf 1 oder 2 (einstellbar), nochmal antippen auf 0. Mehr über die Kartenansicht.
- Filter: Alle, Habe ich, Fehlen, 1 von 2, Zum Tauschen, ★ Wunsch – jeweils mit Anzahl. Sortieren nach Nummer, Name, Seltenheit oder Anzahl.
- **Decks:** Deckliste einfügen (Anzahl, Name, optional Set + Nummer, deutsch oder englisch). Das Tool zeigt, welche Karten du hast – auch in anderer Version –, was fehlt, aus welchem Pack es kommt und was es an Pack-Punkten kostet. Fehlende Karten lassen sich mit einem Klick auf die Wunschliste setzen.
- **Wunschliste:** Karten mit ☆ markieren. Eigene Übersicht mit Bezugsquelle, Suchliste zum Kopieren, und der Pack-Berater kann nach Wunschkarten sortieren.

**Überall**
- In der Set-Ansicht zum vorherigen / nächsten Set springen, in der Kartenansicht zur vorherigen / nächsten Karte (Knöpfe, Pfeiltasten ← →, am Handy wischen).
- Filter und Sortierung werden gemerkt.

## Packs, die es nicht mehr gibt

Zeitlich begrenzte Packs stehen oben im Code von `index.html` in der Liste `PACK_END` (Suche nach „Pack-Verfügbarkeit“):

```js
const PACK_END = {
  'A4b|*': { until: null },                          // Deluxepack-ex – schon weg
  'B4b|*': { until: '2026-10-29T01:59:00+01:00' },   // Deluxepack: Mega – bis 29.10.2026, 01:59 Uhr
};
```

`*` steht für alle Packs des Sets. Für einen neuen Eintrag das Set-Kürzel (steht in jeder Set-Kachel) und das Enddatum eintragen. Winterzeit ist `+01:00`, Sommerzeit `+02:00`. Ab dem Zeitpunkt zählt das Pack im Pack-Berater nicht mehr mit und wird überall als „nicht mehr erhältlich“ markiert. Vorher steht dort „⏳ nur noch bis …“.

## Neue Sets, bevor die Datenbank sie hat

`extra-sets.json` enthält vorläufige Kartenlisten für Sets, die in der Pocket-Datenbank noch fehlen (aktuell Dual Fusion `C1` und Spezialpack Erste Partner `SP1`, Quelle: Serebii). Sobald die Datenbank ein Set selbst enthält, wird der Eintrag dort automatisch ignoriert. Deine Einträge bleiben erhalten, solange Set-Kürzel und Kartennummern gleich sind.

## Datenquellen

- [TCGdex](https://tcgdex.dev) – Karten, Bilder, Preise (Cardmarket)
- [pokemon-tcg-pocket-database](https://github.com/flibustier/pokemon-tcg-pocket-database) – Pocket-Packs, Zieh-Raten, Pack-Punkte
- [Serebii](https://www.serebii.net/tcgpocket/) – vorläufige Kartenlisten und Raten neuer Sets (`extra-sets.json`)
- [PokeAPI](https://github.com/PokeAPI/pokeapi) – deutsche Pokémon-Namen (`pokemon-namen.json`) für Pocket-Karten, zu denen TCGdex noch keine deutschen Daten hat

Neue Sets erscheinen automatisch, sobald die Datenquellen aktualisiert sind – am Tool muss nichts geändert werden.

Inoffizielles Fan-Projekt. Pokémon © Nintendo / Creatures / GAME FREAK.
