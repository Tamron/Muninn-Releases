<div align="center">

# 🐦‍⬛ Muninn

### Zeiterfassung, die in deiner Menüleiste lebt

Eine native **macOS-Menüleisten-App** zum Erfassen von Arbeitszeiten – mit
Umsatzrechnung, automatischen Zuschlägen, Ein-Klick-Übertragung ins
Abrechnungsportal, OneDrive-Backup und eingebautem Auto-Updater.

![macOS 14+](https://img.shields.io/badge/macOS-14%2B-A1A1AA?logo=apple)
![Download](https://img.shields.io/badge/Download-Releases-32CE6A)

</div>

> **Release-Repo:** Hier liegen ausschließlich die fertigen App-Versionen zum
> Download. Der Quellcode ist privat.

---

## ✨ Funktionen

- ⏱️ **Schnelle Zeiterfassung** – Kunde, Datum, Start/Ende, Pause, Einsatzort
  (Vor Ort / Remote) und Beschreibung. Zeit-Auto-Format (`10` → `10:00`) mit
  15-Minuten-Raster.
- 🗂️ **Kunden & Stundensätze** – pro Kunde eigene Sätze für drei Skill-Level
  (System Engineer, Consultant, IT Business Architect); zuletzt genutztes Level
  wird gemerkt.
- 📅 **Abrechnungsmonat entkoppelt vom Arbeitsdatum** – Arbeit vom 28.05. kann
  z. B. in den Juni abgerechnet werden; abweichende Monate sind farblich markiert.
- 💶 **Umsatz & Zuschläge** – laufender Monatsumsatz im Header, Aufschlüsselung
  pro Kunde × Skill. Zuschläge **minutengenau**:
  Spät +25 %, Nacht +50 %, Samstag +50 %/+75 %, Sonntag +100 %, **Feiertag +125 %**.
- ✏️ **Einträge bearbeiten & löschen** – direkt in der App, gruppiert nach
  Kunde × Skill.
- 📝 **Vorlagen** – wiederkehrende Beschreibungstexte speichern und per Klick einfügen.
- 🤖 **Automatische Übertragung** – ein Klick überträgt die erfassten Zeiten per
  Browser-Automation in euer Web-Abrechnungsportal (eintragen oder eintragen +
  abschließen). Vorhandene Einträge werden erkannt und nicht doppelt angelegt.
- ☁️ **OneDrive-Backup** – sichert Kunden, Vorlagen und alle Zeit-CSVs automatisch
  bei jeder Änderung.
- ⬆️ **Auto-Updater** – neue Versionen direkt aus der App installieren
  (Einstellungen → Updates), ohne die alte App zu löschen.
- 📄 **Offene, lokale Daten** – JSON (Kunden, Vorlagen) und CSV (Zeiten) in einem
  frei wählbaren Ordner. Keine Cloud-Pflicht, kein Login, kein Tracking.

---

## ⬇️ Installation

1. Unter **[Releases](../../releases/latest)** die neueste `Muninn-<version>.zip`
   herunterladen und entpacken.
2. **`Muninn.app`** in deinen persönlichen Programme-Ordner ziehen:
   Finder → „Gehe zu" → „Gehe zu Ordner…" → **`~/Applications`** eingeben.
   _(Kein Admin nötig; nur von dort kann sich die App selbst aktualisieren.)_
3. **Einmalig** im Terminal die Download-Markierung entfernen – sonst blockt
   macOS die App („Apple konnte nicht überprüfen …"):
   ```bash
   xattr -dr com.apple.quarantine ~/Applications/Muninn.app
   ```
   _(Kein Admin-Recht nötig.)_
4. **`Muninn.app`** per Doppelklick öffnen – fertig.

> **Warum der Terminal-Schritt?** Die App ist ohne kostenpflichtiges
> Apple-Entwicklerkonto signiert. Auf macOS 15/26 gibt es kein
> „Rechtsklick → Öffnen" mehr, und auf verwalteten Macs ist „Dennoch öffnen"
> oft gesperrt – der `xattr`-Befehl ist der zuverlässige, admin-freie Weg.
> Er ist **nur beim ersten Mal** nötig; künftige Updates entfernen die
> Markierung automatisch.

### Terminal öffnen?
Spotlight (`⌘ + Leertaste`) → „Terminal" tippen → Enter. Befehl aus Schritt 3
hineinkopieren und mit Enter ausführen.

---

## 🔄 Updates

Muninn aktualisiert sich **selbst**: beim Start wird geprüft, manuell geht es
über **Einstellungen → Updates → „Nach Updates suchen"**. Ein Klick auf
**„Jetzt aktualisieren"** lädt die neue Version, tauscht die App aus und startet
sie neu – kein manuelles Nachinstallieren.

---

## 🐍 Automatische Übertragung einrichten (optional)

Nur nötig, wenn du die **automatische Übertragung ins Web-Portal** nutzen willst.
Die Zeiterfassung selbst funktioniert auch ohne.

Voraussetzungen: **Python 3**, das Python-Paket **`selenium`** und **Google Chrome**.

1. **Python 3 installieren** (eine Variante genügt):
   - Apple-Variante: im Terminal `xcode-select --install` ausführen → liefert
     `/usr/bin/python3`, **oder**
   - Installer von [python.org](https://www.python.org/downloads/macos/) (legt
     üblicherweise `/usr/local/bin/python3` an), **oder**
   - per Homebrew: `brew install python` (legt `/opt/homebrew/bin/python3` an).
2. **selenium installieren** – im Terminal:
   ```bash
   python3 -m pip install selenium
   ```
3. **Google Chrome installieren** (falls noch nicht vorhanden).
4. **Python-Pfad in der App setzen:** Muninn öffnen → **Zahnrad (Einstellungen)
   → Abrechnung → Python**. Standard ist `/usr/bin/python3`. Hast du Python woanders
   installiert, hier den passenden Pfad eintragen (über den **„…"-Knopf** auswählbar),
   z. B. `/usr/local/bin/python3` oder `/opt/homebrew/bin/python3`.

> Die nötigen Automations-Skripte sind **in der App enthalten** – du musst keine
> zusätzlichen Dateien ablegen. Beim ersten Lauf öffnet sich ein Terminal-Fenster
> und Chrome; du loggst dich im Portal ein, den Rest macht die App.

---

## 🚀 Erster Start

Beim allerersten Öffnen ist die App **leer** – das ist normal:

- Standard-Speicherort ist **`~/Desktop/DLNs`** (in den Einstellungen änderbar).
  Der Ordner wird automatisch angelegt.
- Es sind **noch keine Kunden** hinterlegt. Lege über das **„+"** im Kunden-Dropdown
  deine Kunden mit Stundensätzen an – danach kannst du Zeiten erfassen.
- Es werden **keine Setup-Dateien** vorausgesetzt; fehlt etwas, startet die App
  einfach mit leeren Listen.

---

## 🖥️ Systemvoraussetzungen

- **macOS 14 (Sonoma)** oder neuer
- _(optional, nur für die automatische Übertragung)_ Python 3 + `selenium` + Google Chrome

---

<div align="center">
<sub>🐦‍⬛ Muninn – benannt nach Odins Raben für das Gedächtnis.</sub>
</div>
