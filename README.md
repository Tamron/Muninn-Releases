<div align="center">

# 🐦‍⬛ Muninn

### Zeiterfassung, die in deiner Menüleiste lebt

Native macOS-Menüleisten-App für IT-Dienstleister: Arbeitszeiten pro Kunde
erfassen, Monatsumsatz inklusive Zuschlägen auswerten und die Zeiten auf Wunsch
automatisiert ins Web-Abrechnungsportal übertragen – **klassische Projekte und
DLV (Dienstleistungsverträge / Professional Service)**.

[![Version](https://img.shields.io/badge/Version-2.0.0-60A5FA?style=for-the-badge)](../../releases/latest)
[![Download](https://img.shields.io/badge/Download-Muninn.zip-32CE6A?style=for-the-badge)](../../releases/latest)
[![macOS](https://img.shields.io/badge/macOS-14%2B-A1A1AA?style=for-the-badge&logo=apple)](../../releases/latest)

</div>

---

Muninn erfasst Arbeitszeiten pro Kunde, wertet den Monatsumsatz inklusive
Zuschlägen aus und überträgt die Zeiten auf Wunsch automatisiert ins
Web-Abrechnungsportal. **Sämtliche Daten bleiben lokal** – kein Konto, kein
Cloud-Zwang, kein Tracking; ein Backup nach OneDrive ist optional.

Dieses Repository stellt die fertigen App-Versionen zum Download bereit. Der
Quellcode liegt in einem separaten, privaten Repository.

---

## ✨ Funktionen

### ⏱️ Erfassung
- **Schnelle Zeiteinträge** mit Kunde, Datum, Start/Ende, Pause, Einsatzort
  (vor Ort oder remote) und Beschreibung.
- **Eingebaute Stoppuhr** – Timer direkt im Kopfbereich starten und stoppen; die
  gestoppte Dauer wird auf die nächste Viertelstunde aufgerundet und als
  Start/Ende übernommen, „Verwerfen" verwirft die Aufzeichnung wieder.
- **Eintrag duplizieren** – einen bestehenden Eintrag als Vorlage ins Formular
  übernehmen.
- **Überlappungs-Warnung** – überschneidet sich die Zeit mit einem bestehenden
  Eintrag desselben Tages, weist ein dezenter Hinweis darauf hin.
- **Live-Vorschau der Zuschläge** – schon beim Tippen Summe aus Stunden und
  Betrag, auf Wunsch aufgeschlüsselt nach Zuschlagszone.
- **Anfahrt bei „Vor Ort"** – zusätzliche Felder für Kilometer und Anfahrtszeit.
- **Auto-Format & Validierung** – Uhrzeiten werden beim Tippen formatiert und
  gegen ein 15-Minuten-Raster geprüft; Pausen akzeptieren Komma und Punkt.
- **Tätigkeits-Vorlagen** – wiederkehrende Beschreibungen per Klick einfügen.
- **Bearbeiten & löschen** – erfasste Einträge nachträglich ändern, gruppiert
  nach Kunde und Skill-Level.
- **Volltextsuche** – Beschreibungen über alle Monate des laufenden Jahres
  durchsuchen.

### 🗂️ Kunden, Skill-Level & DLV
- Beliebig viele Kunden mit **eigenen Stundensätzen je Skill-Level**
  (System Engineer, Consultant, IT Business Architect).
- **DLV pro Kunde aktivierbar** – ein Schalter im Kunden-Dialog schaltet die
  Abrechnungsform **DLV (Dienstleistungsverträge / Professional Service)** frei,
  inklusive eigenem Stundensatz für *DLV · System Engineer*.
- **Optionale Auftragsnummer + Alias** – unterscheidet gleichnamige Kunden.
- Das **zuletzt genutzte Skill-Level** wird pro Kunde gemerkt.

### 📊 Auswertung & Umsatz
- **Laufender Monatsumsatz** stets im Kopfbereich sichtbar.
- **Detailansicht** pro Kunde und Skill-Level, über alle Monate navigierbar.
- **Jahres-Diagramm** – Umsatz oder Stunden über zwölf Monate auf einen Blick.
- **Monatsabschluss-Übersicht** – Status je Kunde und Skill (offen, eingetragen,
  erledigt), Plausibilitätsprüfung (fehlende Werktage, auffällig lange Tage) und
  Vergleich von Stunden und Umsatz zum Vormonat.
- **Zuschläge minutengenau:** Spät (+25 %), Nacht (+50 %), Samstag (+50 %/+75 %),
  Sonntag (+100 %), gesetzliche Feiertage (+125 %).
- **Abrechnungsmonat entkoppelt vom Arbeitsdatum** – Zeiten frei einem Monat
  zuordnen.
- **Farb-Markierung** nach dem Abrechnen: grün = eingetragen, blau = erledigt.
- **Vormonat-Erinnerung** – sind im Vormonat noch Kunden offen, weist ein
  schließbares Banner darauf hin.

### 🤖 Abrechnung (automatisiert)
- **Ein Klick** überträgt die erfassten Zeiten per Browser-Automation ins
  Web-Abrechnungsportal – wahlweise nur eintragen oder eintragen und abschließen.
- **Zwei Abrechnungsformen:** klassische **Projekte** *und* **DLV**. Die App
  wählt anhand des Skill-Levels automatisch den passenden Ablauf – beide laufen
  im selben Abrechnungs-Fenster.
- **Ein Fenster für alles** – einmal anmelden, beliebig viele Kunden abrechnen;
  keine gespeicherten Zugangsdaten.
- **Mehrere auf einmal** – mehrere Kunden/Skills gemeinsam abrechnen.
- **Keine Dubletten** – bereits vorhandene Einträge werden erkannt und
  übersprungen.

### 🖥️ Oberfläche & Bedienung
- **Hell- und Dunkel-Modus** – per Schalter in den Einstellungen umschaltbar.
- **Globaler Hotkey** – öffnet Muninn aus jeder App direkt im Erfassungsformular;
  Tastenkombination frei wählbar.
- **Popover anheften** – das Fenster bleibt beim Klick außerhalb geöffnet.

### ☁️ Daten, Backup & Updates
- Alle Daten lokal als JSON (Kunden, Vorlagen) und CSV (Zeiten) in einem frei
  wählbaren Ordner.
- Optionales **OneDrive-Backup** – sichert automatisch bei jeder Änderung.
- **Integrierter Updater** – neue Versionen direkt aus der App installieren.

---

## 🚀 Installation

1. Aktuelle `Muninn-<version>.zip` aus den [Releases](../../releases/latest)
   herunterladen und entpacken.
2. `Muninn.app` nach `~/Applications` verschieben.
3. Quarantäne-Markierung des Downloads entfernen:
   ```bash
   xattr -dr com.apple.quarantine ~/Applications/Muninn.app
   ```
4. Muninn per Doppelklick öffnen.

Schritt 3 ist nötig, weil die App ohne kostenpflichtiges Apple-Entwicklerkonto
signiert ist und macOS sie sonst beim ersten Start blockiert. Bei späteren
Versionen entfällt er – der integrierte Updater entfernt die Markierung selbst.

## 👋 Erster Start

Beim ersten Start ist Muninn leer und legt seinen Datenordner unter
`~/Desktop/DLNs` an (in den Einstellungen änderbar). Über das Kunden-Dropdown
werden Kunden mit ihren Stundensätzen angelegt – bei Bedarf inklusive
DLV-Vertrag –, anschließend lassen sich Zeiten erfassen.

## ⚙️ Abrechnung einrichten (optional)

Die automatische Übertragung setzt Python 3, das Paket `selenium` und Google
Chrome voraus. Die Zeiterfassung selbst funktioniert unabhängig davon.

1. Python 3 installieren – etwa über `xcode-select --install`, den Installer von
   [python.org](https://www.python.org/downloads/macos/) oder Homebrew.
2. `selenium` ergänzen:
   ```bash
   python3 -m pip install selenium
   ```
3. Google Chrome installieren.
4. In den Einstellungen unter „Abrechnung" den **Python-Pfad** auf das Python
   mit `selenium` setzen.

Die benötigten Automations-Skripte sind in der App enthalten.

## 🖥️ Systemvoraussetzungen

- macOS 14 (Sonoma) oder neuer
- Für die automatische Übertragung zusätzlich: Python 3, `selenium`, Google Chrome

---

<div align="center">
<sub>🐦‍⬛ Muninn – benannt nach Odins Raben für das Gedächtnis.</sub>
</div>
