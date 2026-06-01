# 🐦‍⬛ Muninn

Native macOS-Menüleisten-App zur Zeiterfassung für IT-Dienstleister. Muninn
erfasst Arbeitszeiten pro Kunde, wertet den Monatsumsatz inklusive Zuschlägen aus
und überträgt die Zeiten auf Wunsch automatisiert in ein Web-Abrechnungsportal.
Sämtliche Daten bleiben lokal; eine Sicherung nach OneDrive ist optional.

Dieses Repository stellt die fertigen App-Versionen zum Download bereit. Der
Quellcode liegt in einem separaten, privaten Repository.

## Funktionen

### Erfassung
- Zeiteinträge mit Kunde, Datum, Start- und Endzeit, Pause, Einsatzort (vor Ort
  oder remote) und Beschreibung.
- Uhrzeiten werden beim Tippen automatisch formatiert und gegen ein
  15-Minuten-Raster geprüft; Pausenangaben akzeptieren Komma und Punkt.
- Wiederkehrende Beschreibungen lassen sich als Vorlagen ablegen und mit einem
  Klick einfügen.
- Erfasste Einträge sind nachträglich editier- und löschbar, gruppiert nach
  Kunde und Skill-Level.

### Kunden und Stundensätze
- Beliebig viele Kunden, jeder mit eigenen Stundensätzen je Skill-Level
  (System Engineer, Consultant, IT Business Architect).
- Das zuletzt genutzte Skill-Level wird pro Kunde gemerkt.

### Auswertung und Umsatz
- Der laufende Monatsumsatz ist im Kopfbereich stets sichtbar.
- Eine Detailansicht schlüsselt den Umsatz pro Kunde und Skill-Level auf und ist
  über alle Monate navigierbar.
- Zuschläge werden minutengenau ermittelt: Spätarbeit (+25 %), Nacht (+50 %),
  Samstag (+50 % / +75 %), Sonntag (+100 %) und gesetzliche Feiertage (+125 %).
- Der Abrechnungsmonat ist vom Arbeitsdatum entkoppelt; Zeiten lassen sich so
  frei einem Monat zuordnen.

### Abrechnung
- Übertragung der erfassten Zeiten in ein Web-Abrechnungsportal per
  Browser-Automation – wahlweise nur eintragen oder eintragen und abschließen.
- Bereits vorhandene Einträge werden anhand von Datum und Startzeit erkannt und
  nicht doppelt angelegt.

### Daten, Backup und Updates
- Alle Daten liegen lokal als JSON (Kunden, Vorlagen) und CSV (Zeiten) in einem
  frei wählbaren Ordner – ohne Konto, Cloud-Zwang oder Tracking.
- Ein optionales Backup nach OneDrive sichert Kunden, Vorlagen und Zeit-CSVs
  automatisch bei jeder Änderung.
- Neue Versionen installiert ein integrierter Updater direkt aus der App.

## Installation

1. Aktuelle `Muninn-<version>.zip` aus den [Releases](../../releases/latest)
   herunterladen und entpacken.
2. `Muninn.app` nach `~/Applications` verschieben.
3. Quarantäne-Markierung des Downloads entfernen:
   ```bash
   xattr -dr com.apple.quarantine ~/Applications/Muninn.app
   ```
4. Muninn per Doppelklick öffnen.

Schritt 3 ist erforderlich, weil die App ohne kostenpflichtiges
Apple-Entwicklerkonto signiert ist und macOS sie sonst beim ersten Start
blockiert. Bei späteren Versionen entfällt er, da der integrierte Updater die
Markierung selbst entfernt.

## Erster Start

Beim ersten Start ist Muninn leer und legt seinen Datenordner unter
`~/Desktop/DLNs` an (in den Einstellungen änderbar). Über das Kunden-Dropdown
werden Kunden mit ihren Stundensätzen angelegt; anschließend lassen sich Zeiten
erfassen.

## Abrechnung einrichten (optional)

Die automatische Übertragung setzt Python 3, das Paket `selenium` und Google
Chrome voraus. Die Zeiterfassung selbst funktioniert unabhängig davon.

1. Python 3 installieren – etwa über `xcode-select --install`, den Installer von
   [python.org](https://www.python.org/downloads/macos/) oder Homebrew.
2. `selenium` ergänzen:
   ```bash
   python3 -m pip install selenium
   ```
3. Google Chrome installieren.
4. In den Einstellungen unter „Abrechnung“ den Python-Pfad prüfen
   (Standard `/usr/bin/python3`).

Die benötigten Automations-Skripte sind in der App enthalten.

## Systemvoraussetzungen

- macOS 14 (Sonoma) oder neuer
- Für die automatische Übertragung zusätzlich: Python 3, `selenium`, Google Chrome
