# Screen-Ellophant update-guideline

# 🚀 Release & Update Workflow | Screen Ellophant

Diese Dokumentation beschreibt den präzisen Prozess, um eine neue Version von **Screen Ellophant** zu veröffentlichen und die automatische Update-Funktion (Tauri Updater) zu aktualisieren.

---

## 🛠 Vorbereitung (Versionierung)

Bevor ein Release erstellt wird, muss die Versionsnummer konsistent über alle Konfigurationsdateien hinweg aktualisiert werden. Das Format folgt dem **Semantic Versioning**: `x.x.x`.

### 1. Versionsnummern anpassen
Stelle sicher, dass die neue Version in den folgenden Dateien identisch eingetragen ist:

- [ ] **`updater.json`**: Version an 3 Stellen aktualisieren (Top-Level & Plattform-Einträge).
- [ ] **`package.json`**: `version`-Feld anpassen.
- [ ] **`package-lock.json`**: Wird meist automatisch durch `npm version` angepasst, sonst manuell prüfen.
- [ ] **`src-tauri/tauri.conf.json`**: `version`-Feld unter `package` aktualisieren.
- [ ] **`StartingWindow/index.html`**: Sichtbare Anzeige der Version für den User anpassen.

---

## 🏗 Build-Prozess (GitHub Actions)

Sobald die Dateien vorbereitet sind, wird der Build-Prozess auf GitHub durch einen Git-Tag ausgelöst.

### 2. Änderungen committen
```bash
git add .
git commit -m "build vx.x.x"
git push
