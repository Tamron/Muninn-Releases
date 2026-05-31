# Muninn

Eine native **macOS-Menüleisten-App zur Zeiterfassung** – internes Team-Tool.

> Dies ist das **Release-Repo**: es enthält ausschließlich die fertigen
> App-Versionen zum Download. Der Quellcode liegt in einem separaten,
> privaten Repository.

## Installation

1. Unter **[Releases](../../releases/latest)** die neueste `Muninn-<version>.zip` herunterladen und entpacken.
2. **`Muninn.app`** in den Ordner **`~/Applications`** ziehen
   (der persönliche Programme-Ordner in deinem Benutzerverzeichnis).
3. **Einmalig** im Terminal die Download-Markierung entfernen – sonst blockt
   macOS die App („Apple konnte nicht überprüfen …"):
   ```bash
   xattr -dr com.apple.quarantine ~/Applications/Muninn.app
   ```
   (Kein Admin-Recht nötig.)
4. **`Muninn.app`** per Doppelklick öffnen.

> Hintergrund: Die App ist ohne kostenpflichtiges Apple-Entwicklerkonto
> signiert. Der Terminal-Schritt ist nur beim **ersten** Mal nötig – alle
> künftigen Updates installiert Muninn selbst (und entfernt die Markierung
> dabei automatisch).

## Updates

Muninn aktualisiert sich **selbst**. Beim Start sucht die App nach neuen
Versionen; du kannst auch jederzeit manuell unter **Einstellungen → Updates →
„Nach Updates suchen"** prüfen. Ein Klick auf **„Jetzt aktualisieren"** lädt die
neue Version, tauscht die App aus und startet sie neu – kein manuelles
Nachinstallieren nötig.

## Systemvoraussetzungen

- macOS 14 (Sonoma) oder neuer
